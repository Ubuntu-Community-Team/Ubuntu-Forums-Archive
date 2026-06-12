---
title: "Is it still possible to set up Ubuntu 18.04 as an AD Domain Controller?"
date: 2020-01-21
forum: Server Platforms
---

### Post by chameleonthegeek on 2020-01-21
I have successfully set up Xenial as a DC, and have had two Xenial DCs running beautifully at separate sites for more than two years.  Once I figured it out, I created a script which asked all the right questions and was well-documented with my learnings as I set up the process.  Both running servers were initially configured solely by the script, from first boot to functional DC.  Each was further configured after domain provisioning succeeded.

I am now attempting to duplicate this process using Bionic.  I need to deploy a new DC.  Both Xenial and Bionic are now failing at the same point, which indicates that something has changed in the larger environment. Since I need a new DC, it only makes sense to use Bionic if at all possible.  I have parsed through each of the dozen-plus blogs, tutorials and videos regarding this process (all on Bionic, as recent as 11/2019), and have met brick walls on each.  First - it is clear in each one that the author has performed some configuration on the system prior to documenting the process, and don't indicate what those pre-tutorial configuration steps are.  Second - the author either has no mechanism for comment/question on the process, or is now so bored with the process that they ignore any comments or questions, so there is no way to learn from the author what other steps they took to prevent the failures I am encountering.

I've been able to install and configure Samba as a File Server on Bionic, but the process fails if I attempt to provision Samba as a DC.  The failure message itself leaves me asking a few questions as I walk through the full text and context of the error.  First - the failure demonstrates that the installer is using Python 2.7.  Python 2.7 isn't even installed on the system until I install Samba.  Is Samba still Python 2.7 based, or am I missing something to ensure that it pulls/uses Python 3.x code?  It is possible that if I fix the former, I'll fix the fact that the Python function that throws the error is [COLOR=#242729][FONT=Arial]samba.[/FONT][/COLOR]**samba3**[COLOR=#242729][FONT=Arial].smbd.set_nt_acl, while it is trying to provision the domain on a Samba 4 install?  Or is Samba 4 still utilizing a significant amount of Samba3 python code?

Failure text:
[/FONT][/COLOR]```
Setting up self join
set_nt_acl_no_snum: fset_nt_acl returned NT_STATUS_NOT_SUPPORTED.
ERROR(runtime): uncaught exception - (-1073741637, 'The request is not supported.')
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 176, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/domain.py", line 474, in run
    nosync=ldap_backend_nosync, ldap_dryrun_mode=ldap_dryrun_mode)
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 2175, in provision
    skip_sysvolacl=skip_sysvolacl)
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 1806, in provision_fill
    names.domaindn, lp, use_ntvfs)
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 1593, in setsysvolacl
    service=SYSVOL_SERVICE)
  File "/usr/lib/python2.7/dist-packages/samba/ntacls.py", line 162, in setntacl
    smbd.set_nt_acl(file, security.SECINFO_OWNER | security.SECINFO_GROUP | security.SECINFO_DACL | security.SECINFO_SACL, sd, service=service)
```

[COLOR=#242729][FONT=Arial][FONT=inherit]Am I missing something in the drive mounting parameters? tune2fs reports[/FONT]

```
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Default mount options:    user_xattr acl
```

[/FONT]I've attempted to research this through the Samba.org website, but every indication I'm seeing is that this process should just work ([https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller))[FONT=Consolas].  I've been unable to find any kind of forum dedicated to Samba where I could search for similar questions and associated suggestions or ask the questions myself.[/FONT][FONT=Arial]
[/FONT][/COLOR]

---

### Post by LHammonds on 2020-01-24
I think you are going about it in the wrong order.  When provisioning a new domain, all samba configs need to be wiped.

I started to document how to setup a controller but got side-tracked and never finished it but here is what I had (which I cannot say if it is the best way to do it as I have not finished it yet)

[https://hammondslegacy.com/forum/viewtopic.php?f=40&t=235](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=235)

LHammonds

---

