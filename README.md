# HTML::FormFu

[![CI](https://github.com/uperl/HTML-FormFu/actions/workflows/ci.yml/badge.svg)](https://github.com/uperl/HTML-FormFu/actions/workflows/ci.yml)

HTML::FormFu is a Perl form framework that aims to be as easy as possible to
use for basic web forms, but with the power and flexibility to do anything
else you might want to do (as long as it involves forms).

Forms are defined in a config file (YAML, JSON, or anything supported by
[Config::Any](https://metacpan.org/pod/Config::Any)), or built directly in
Perl. HTML::FormFu handles rendering, filtering, constraints, validation,
and re-populating a form with submitted values and errors — with sane,
customizable "XHTML 1.0 Strict" output out of the box.

## Quick example

```perl
use HTML::FormFu;

my $form = HTML::FormFu->new;

$form->load_config_file('form.yml');

$form->process($cgi_query);

if ( $form->submitted_and_valid ) {
    # do something with $form->params
}
else {
    # display the form
    $template->param( form => $form );
}
```

```yaml
---
action: /login
indicator: submit
auto_fieldset: 1

elements:
  - type: Text
    name: user
    constraints:
      - Required

  - type: Password
    name: pass
    constraints:
      - Required

  - type: Submit
    name: submit

constraints:
  - SingleValue
```

## Installation

```
cpanm HTML::FormFu
```

## Documentation

The full manual — every element, constraint, filter, and configuration
option — lives in the module's POD and is browsable on
[MetaCPAN](https://metacpan.org/pod/HTML::FormFu) or via `perldoc HTML::FormFu`
after installing.

## License

This library is free software and may be distributed under the same terms
as Perl itself (the Perl 5 license).
