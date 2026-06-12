---
title: "Error when running ansible-playbook from ubuntu20.04 ansible server to ubuntu24.04"
date: 2024-05-12
forum: Server Platforms
---

### Post by masato-d on 2024-05-12
When running ansible on a newly installed ubuntu 24.04 from an ansible server built with ubuntu 20.04, the following error occurs and it cannot be executed.
I think this is because the version of ansible provided for ubuntu20.04 is old, 2.9.6, and is not compatible with python3.12.


If you have ansible installed on ubuntu24.04, you can run it.


24.04 -> 20.04 OK
24.04 -> 24.04 OK
20.04 -> 22.04 OK
20.04 -> 24.04NG


The problem is that it is not possible to build a system from 22.04 to 24.04.
```
PLAY [Change Hosts] *****************************************************************************************************************************************************************


TASK [Gathering Facts] **************************************************************************************************************************************************************
fatal: [ubuntu-tar]: FAILED! => {"ansible_facts": {}, "changed": false, "failed_modules": {"setup": {"ansible_facts": {"discovered_interpreter_python": "/usr/bin/python3"}, "exception": "Traceback (most recent call last):\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 102, in <module>\r\n    _ansiballz_main()\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 94, in _ansiballz_main\r\n    invoke_module(zipped_mod, temp_path, ANSIBALLZ_PARAMS)\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 37, in invoke_module\r\n    from ansible.module_utils import basic\r\n  File \"/tmp/ansible_setup_payload_e17q1rns/ansible_setup_payload.zip/ansible/module_utils/basic.py\", line 171, in <module>\r\nModuleNotFoundError: No module named 'ansible.module_utils.six.moves'\r\n", "failed": true, "module_stderr": "Shared connection to 192.168.222.162 closed.\r\n", "module_stdout": "Traceback (most recent call last):\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 102, in <module>\r\n    _ansiballz_main()\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 94, in _ansiballz_main\r\n    invoke_module(zipped_mod, temp_path, ANSIBALLZ_PARAMS)\r\n  File \"/root/.ansible/tmp/ansible-tmp-1715506968.0486069-181617743508076/AnsiballZ_setup.py\", line 37, in invoke_module\r\n    from ansible.module_utils import basic\r\n  File \"/tmp/ansible_setup_payload_e17q1rns/ansible_setup_payload.zip/ansible/module_utils/basic.py\", line 171, in <module>\r\nModuleNotFoundError: No module named 'ansible.module_utils.six.moves'\r\n", "msg": "MODULE FAILURE\nSee stdout/stderr for the exact error", "rc": 1}}, "msg": "The following modules failed to execute: setup\n"}


PLAY RECAP **************************************************************************************************************************************************************************
ubuntu-tar                 : ok=0    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0

```


Manually run the ansible script left locally.

```
Traceback (most recent call last):
  File "/root/.ansible/tmp/ansible-tmp-1715503930.0680447-93623894992085/AnsiballZ_setup.py", line 247, in <module>
    _ansiballz_main()
  File "/root/.ansible/tmp/ansible-tmp-1715503930.0680447-93623894992085/AnsiballZ_setup.py", line 237, in _ansiballz_main
    invoke_module(zipped_mod, temp_path, ANSIBALLZ_PARAMS)
  File "/root/.ansible/tmp/ansible-tmp-1715503930.0680447-93623894992085/AnsiballZ_setup.py", line 104, in invoke_module
    from ansible.module_utils import basic
  File "/tmp/ansible_setup_payload_umcg_j9w/ansible_setup_payload.zip/ansible/module_utils/basic.py", line 171, in <module>
ModuleNotFoundError: No module named 'ansible.module_utils.six.moves'

```

---

### Post by masato-d on 2024-05-12
It was the same from 22.04 ansible (2.10.7) to 24.04.

---

### Post by TheFu on 2024-05-12
Ansible constantly changes and deprecates features while adding new all-the-time.

BTW, would really help if you posted terminal output inside forum code-tags for readability.  Ansible output is readable and formatted in a way that can be easily read when whiltespace is retained.   Too hard to read otherwise.  Don't make it hard for someone to help you.

 Code Tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by MAFoElffen on 2024-05-12
+1 on the Code Tags...

Edit post > Go Advanced > Select text with mouse > Press the "#" icon in the Advanced Editor Menu Bar... Will add the tags around the selected text.

Are these on new 24.04 images or upgrading them from previous to, to (now) released 24.04 with Ansible? (I can confirm that path is not opened up yet.) Or just any kind of scripted management from Ansible on those versions?

---

### Post by masato-d on 2024-05-14
This is a newly installed ubuntu24.04.

---

### Post by TheFu on 2024-05-14
Is 24.04 the ansible target or the Ansible host system?

My Ansible host run **ansible 2.10.8** on a 22.04-based workstation.  I haven't pointed it at any 24.04 systems yet.

---

### Post by masato-d on 2024-05-17
24.04 is the target system.

---

### Post by TheFu on 2024-05-17
> **masato-d said:**
> 24.04 is the target system.

So, I'm able to reproduce the issue and it appears that Ansible 3.10.x is unsupported on 24.04.  That means the repo version of ansible should not be used with 24.04 clients.  


It won't be fixed because the 20.04 LTS is not going to add more features (supporting 24.04 would be a new feature) to avoid breaking existing, working, systems.

I'm in the same situation.

Using ansible from their repo isn't hard, especially since only the ansible workstation would need to be updated, not every client.  Of course, I haven't tried it.  But at least you know why and what is needed to address this issue in your environment, if you choose. there is a risk that 20.04 and older releases may not work with ansible, so plan any changes appropriately.  I've had to run dual backup servers when my backup tool bridge python versions a few years ago.  It drove me to migrate quickly from 18.04 up, though I would have preferred to stay on the 10 yr support for 18.04 instead.

As you know, forward compatibility for things that won't exist for 4 yrs in the future is hard.  The easy answer might be just to migration your Ansible workstation to 22.04 and try that first.  If it doesn't work, move it to 24.04.

---

### Post by masato-d on 2024-05-18
Even after upgrading to 22.04, running ansible to 24.04 resulted in an error.
Direct upgrade from 22.04 to 24.04 is not yet available.
Currently, it is not possible to configure settings to check 24.04 after a new installation.
It is possible if you increase it to 22.04->23.10->24.04, but...

---

### Post by TheFu on 2024-05-18
Try a fresh install.

Or just get the newer version of ansible directly from their project page and don't bother with the debian packages.

---

