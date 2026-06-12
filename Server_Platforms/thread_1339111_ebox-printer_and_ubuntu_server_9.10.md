---
title: "ebox-printer and ubuntu server 9.10"
date: 2009-11-27
forum: Server Platforms
---

### Post by jpgeerets on 2009-11-27
hi folks,

im trying to setup a linux server with ebox on it.
install of ubunbtu910 was no problem. all works out of the box.
then i installed ebox to manage the server. installed it by apt-get.
when i installed the module ebox-printers all went well, until i tryed to enable this module.
then i get this error code:
```
A really nasty bug has occurred
Exception
Failed to enable: root command /usr/share//ebox-printers/ebox-printers-enable failed. Error output: invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found. sed: can't read /etc/cups/mime.convs: No such file or directory Command output: . Exit value: 2
Trace
Failed to enable: root command /usr/share//ebox-printers/ebox-printers-enable failed.
Error output: invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
sed: can't read /etc/cups/mime.convs: No such file or directory

Command output: .
Exit value: 2 at /usr/share/perl5/EBox/CGI/ServiceModule/ConfigureModuleController.pm line 74
EBox::CGI::ServiceModule::ConfigureModuleController::_process('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0xba...') called at /usr/share/perl5/EBox/CGI/Base.pm line 261
EBox::CGI::Base::run('EBox::CGI::ServiceModule::ConfigureModuleController=HASH(0xba...') called at /usr/share/perl5/EBox/CGI/Run.pm line 120
EBox::CGI::Run::run('EBox::CGI::Run', 'ServiceModule/ConfigureModuleController', 'EBox') called at /usr/share/ebox/cgi/ebox.cgi line 19
ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler('Apache2::RequestRec=SCALAR(0xba117248)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
ModPerl::RegistryCooker::run('ModPerl::Registry=HASH(0xba7be458)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
ModPerl::RegistryCooker::default_handler('ModPerl::Registry=HASH(0xba7be458)') called at /usr/lib/perl5/ModPerl/Registry.pm line 31
ModPerl::Registry::handler('ModPerl::Registry', 'Apache2::RequestRec=SCALAR(0xba117248)') called at -e line 0
eval {...} called at -e line 0

```

anyone had this before?
any idea how to solve this?

thanks in advanced!

Jean-Paul

---

### Post by foolano on 2009-11-29
Hi, I can confirm the bug.

I'll try to upload a new package to my PPA to fix it. However, the following workaround might work for you:

```

# sudo ln -s /etc/init.d/cups /etc/init.d/cupsys
# sudo touch /etc/cups/mime.convs

```

---

### Post by jpgeerets on 2009-11-30
hi!

this seems to work great!!
for now i can activate the printer module.

but, now next problem... i can not find any printer driver.
when i press the button "add printer", i van choose which port etc.
finaly i can choose what vendor (hp), then i can select the model (in this case dj5652), but, after that i have to choose a driver for the printer...
this is empty.

can this be the same bug as my primary problem?
how should i put drivers into?

thanks in advanced!

Jean-Paul

---

### Post by tenach on 2010-01-14
Hey, I was able to confirm the same error and apply the workaround.  Everything is now working like it should!

Thank you :D

---

