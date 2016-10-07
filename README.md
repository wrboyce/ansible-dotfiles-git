wrboyce.dotfiles-git
====================

[![Build Status](https://travis-ci.org/wrboyce/ansible-dotfiles-git.svg)](https://travis-ci.org/wrboyce/ansible-dotfiles-git)

Manage git client configuration.


Role Variables
--------------

### Basic Usage

It its most basic usage, 8 variables are exposed (2 of which are required) all of which are relatively self-explainatory,
mapping directly to their `git config` counterparts.:

| ansible var | git config var | required? |
|---|---|---|
| gitconfig_user_name | user.name | Y |
| gitconfig_user_email | user.email | Y |
| gitconfig_user_signingkey | user.signingkey | N |
| gitconfig_sendemail_smtpencryption | sendemail.smtpencryption | N |
| gitconfig_sendemail_smtpserver | sendemail.smtpserver | N |
| gitconfig_sendemail_smtpserverport | sendemail.smtpserverport | N |
| gitconfig_sendemail_smtppas | sendemail.smtppass | N |
| gitconfig_sendemail_smtpuser | sendemail.smtpuser | N |

### Advanced Usage

For more advanced usage, the `git_configs` variable defines the config files which should be generated:

    git_configs:
      - test

The specific `gitconfig_` variables are used to defined the sections, options and values for the resultant file:

    gitconfig_test:
        section one:
            key1a: val1a
            key2b: val1b
        section 2:
            key2: val2

Would result in a single `gitconfig.d/test.conf`

    [section one]
        key1a = val1a
        key2b = val2b
    [section 2]
        key2 = val2

See `defaults/main.yml` for a real-world configuration example.


Example Playbook
----------------

    - hosts: workstations
      roles:
         - wrboyce.dotfiles-git

License
-------

Apache 2.0
