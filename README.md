# Ansible Project Template

## Recommended Directory Layout

This is the recommended directory layout for Ansible projects. It is based on the [Ansible Best Practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#directory-layout) and [Ansible Galaxy Roles](https://galaxy.ansible.com/docs/contributing/creating_role.html#role-directory-structure) documentation.

The file extension for YAML files is `.yaml` as recommended by the official YAML documentation [yaml.org](https://yaml.org/faq.html). The indentation is 2 spaces as recommended by the [Ansible Reference](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html).

```text
inventories/
   production/
      hosts               # inventory file for production servers
      group_vars/
         group1.yaml      # here we assign variables to particular groups
         group2.yaml
      host_vars/
         hostname1.yaml   # here we assign variables to particular systems
         hostname2.yaml

   staging/
      hosts               # inventory file for staging environment
      group_vars/
         group1.yaml      # here we assign variables to particular groups
         group2.yaml
      host_vars/
         stagehost1.yaml  # here we assign variables to particular systems
         stagehost2.yaml


group_vars/
   group1.yaml            # here we assign variables to particular groups
   group2.yaml
host_vars/
   hostname1.yaml         # here we assign variables to particular systems
   hostname2.yaml

library/                  # if any custom modules, put them here (optional)
module_utils/             # if any custom module_utils to support modules, put them here (optional)
filter_plugins/           # if any custom filter plugins, put them here (optional)

site.yaml                 # main playbook
webservers.yaml           # playbook for webserver tier
dbservers.yaml            # playbook for dbserver tier
tasks/                    # task files included from playbooks
   webservers-extra.yaml  # <-- avoids confusing playbook with task files


roles/
   common/               # this hierarchy represents a "role"
      tasks/             #
         main.yaml       #  <-- tasks file can include smaller files if warranted
      handlers/          #
         main.yaml       #  <-- handlers file
      templates/         #  <-- files for use with the template resource
         ntp.conf.j2     #  <------- templates end in .j2
      files/             #
         bar.txt         #  <-- files for use with the copy resource
         foo.sh          #  <-- script files for use with the script resource
      vars/              #
         main.yaml       #  <-- variables associated with this role
      defaults/          #
         main.yaml       #  <-- default lower priority variables for this role
      meta/              #
         main.yaml       #  <-- role dependencies and optional Galaxy info
      library/           # roles can also include custom modules
      module_utils/      # roles can also include custom module_utils
      lookup_plugins/    # or other types of plugins, like lookup in this case

   webtier/              # same kind of structure as "common" was above, done for the webtier role
   monitoring/           # ""
   fooapp/               # ""
```
