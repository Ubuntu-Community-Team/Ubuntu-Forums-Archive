---
title: "IgnoreHidden proftpd not working"
date: 2010-04-27
forum: Server Platforms
---

### Post by andey on 2010-04-27
This is /etc/proftpd/proftpd.conf

```
Include /etc/proftpd/modules.conf
UseIPv6				off
IdentLookups			off
ServerName			"Debian"
ServerType			standalone
DeferWelcome			off
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off
TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"
DenyFilter			\*.*/
Port				21
MaxInstances			30
User				proftpd
Group				nogroup
Umask				022  022
AllowOverwrite			on

<Limit ALL>
IgnoreHidden on
</Limit>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
  QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
  Ratios off
</IfModule>

<IfModule mod_delay.c>
  DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
  ControlsEngine        off
  ControlsMaxClients    2
  ControlsLog           /var/log/proftpd/controls.log
  ControlsInterval      5
  ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
  AdminControlsEngine off
</IfModule>

```

all files still show, anyone know why?
I want to hide all ".hidden" files and folders

screenshot in filezilla:
[Do not have forced view hidden files]
[[img]http://j.imagehost.org/t/0859/screen9.jpg[/img]](http://j.imagehost.org/view/0859/screen9)

---

### Post by cdenley on 2010-04-27
Did you restart proftpd after any configuration changes? Are you sure you're connecting with FTP, not SFTP? What directory listing do you get with the command-line FTP client?

---

### Post by wdaniels on 2010-09-02
> **andey said:**
> <Limit ALL>
IgnoreHidden on
</Limit>

Bit late now probably, but I think you need to use this in connection with a HideFiles in a Directory context. There was a change at some point so that IgnoreHidden does not hide dot files, but the config itself has to define what is "hidden":

```
Bug 2108 - IgnoreHidden should not hide dotfiles
  Dotfiles are now displayed when the -a argument is supplied, even when the
  IgnoreHidden directive is enabled. To replicate the old behavior of hiding
  dotfiles no matter what, use either of the following directives:
    ListOptions "" strict
    HideFiles ^\..*

```

Changing the ListOptions has never worked for me (anyway the default "-l" should not list dot files AFAIK). But this is what I'm using and it seems to work OK:

```
<Directory />
  HideFiles ^\..*
  <Limit ALL>
    IgnoreHidden On
  </Limit>
</Directory>
```

---

### Post by HellMind on 2012-01-30
> **wdaniels said:**
> Bit late now probably, but I think you need to use this in connection with a HideFiles in a Directory context. There was a change at some point so that IgnoreHidden does not hide dot files, but the config itself has to define what is "hidden":

```
Bug 2108 - IgnoreHidden should not hide dotfiles
  Dotfiles are now displayed when the -a argument is supplied, even when the
  IgnoreHidden directive is enabled. To replicate the old behavior of hiding
  dotfiles no matter what, use either of the following directives:
    ListOptions "" strict
    HideFiles ^\..*

```

Changing the ListOptions has never worked for me (anyway the default "-l" should not list dot files AFAIK). But this is what I'm using and it seems to work OK:

```
<Directory />
  HideFiles ^\..*
  <Limit ALL>
    IgnoreHidden On
  </Limit>
</Directory>
```

Thank you,

In resumé
this is enough for me:

#ignore hidden
<Directory />
HideFiles ^\..*
</Directory>

---

