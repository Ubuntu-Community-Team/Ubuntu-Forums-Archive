---
title: "eBox problem with File sharing"
date: 2010-09-27
forum: Server Platforms
---

### Post by flycast on 2010-09-27
Installing file sharing using eBox and get the following error:

> Failed to enable: root command /usr/share//ebox-samba/ebox-samba-enable failed.
Error output: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;quotaoff: Cannot find quota file on / [/dev/mapper/SL24Server-root] to turn quotas on/off.
quotaoff: Cannot find quota file on / [/dev/mapper/SL24Server-root] to turn quotas on/off.
quotaon: Cannot find quota file on / [/dev/mapper/SL24Server-root] to turn quotas on/off.
quotaon: Cannot find quota file on / [/dev/mapper/SL24Server-root] to turn quotas on/off.
invoke-rc.d: initscript quota, action "restart" failed.

Command output: smbd stop/waiting
nmbd stop/waiting
* Restarting Zentyal module: users
...done.
Fstab already set up to use quotas
* Turning off quotas...
...done.
* Checking quotas...
* Warning: user quota not configured in filesystem `/.'
* Warning: group quota not configured in filesystem `/.'
...done.
* Turning on quotas...
.
Exit value: 2 at /usr/share/perl5/EBox/CGI/ServiceModule/ConfigureModuleController.pm line 74
EBox::CGI::ServiceModule::ConfigureModuleController::_process('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Base.pm line 262
EBox::CGI::Base::run('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0x7f...') called at /usr/share/perl5/EBox/CGI/Run.pm line 120
EBox::CGI::Run::run('EBox::CGI::Run', 'ServiceModule/ConfigureModuleController', 'EBox') called at /usr/share/ebox/cgi/ebox.cgi line 35
ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler('Apache2::RequestRec=SCALAR(0x7f614d4505b0)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
ModPerl::RegistryCooker::run('ModPerl::Registry=HASH(0x7f614b328cb0)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
ModPerl::RegistryCooker::default_handler('ModPerl::Registry=HASH(0x7f614b328cb0)') called at /usr/lib/perl5/ModPerl/Registry.pm line 31
ModPerl::Registry::handler('ModPerl::Registry', 'Apache2::RequestRec=SCALAR(0x7f614d4505b0)') called at -e line 0
eval {...} called at -e line 0

Lookis like eBox (Zentyal) needs quotas enabled. How?

---

### Post by whoop on 2010-10-08
Do you get this error while installing the package ebox-samba?

for instance:
sudo aptitude install ebox-samba

---

