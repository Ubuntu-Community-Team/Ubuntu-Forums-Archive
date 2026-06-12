---
title: "ownCloud Infinite Scale error"
date: 2023-03-25
forum: Server Platforms
---

### Post by smit9522 on 2023-03-25
[FONT=Verdana]Hey there,[/FONT]

[FONT=Verdana]System that I use is[/FONT]
[FONT=Verdana]Hardware - raspberry 4b 8gb ram [/FONT]
[FONT=Verdana]OS -  ubuntu server[/FONT]

```
[FONT=Verdana]root@ubuntu:~# lsb_release -a[/FONT]
[FONT=Verdana]No LSB modules are available.[/FONT]
[FONT=Verdana]Distributor ID: Ubuntu[/FONT]
[FONT=Verdana]Description:    Ubuntu 22.10[/FONT]
[FONT=Verdana]Release:        22.10[/FONT]
[FONT=Verdana]Codename:       kinetic[/FONT]

```

[FONT=Verdana]I am trying to install ownCloud inifinte scale from [/FONT][https://github.com/owncloud/ocis](https://github.com/owncloud/ocis)[FONT=Verdana] . So now what is happening is that in the steps it says "make generate" and when I run that code I get errors like this[/FONT]

[FONT=Verdana]```
root@ubuntu:~/ocis# make generate[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/antivirus'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/antivirus'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/app-provider'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/app-provider'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/app-registry'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/app-registry'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/audit'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/audit'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/auth-basic'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/auth-basic'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/auth-bearer'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/auth-bearer'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/auth-machine'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/auth-machine'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/eventhistory'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/eventhistory'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/frontend'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/frontend'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/gateway'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/gateway'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/graph'[/FONT]
[FONT=Verdana]dir pkg/service/v0 --case underscore --name GatewayClient[/FONT]
[FONT=Verdana]dir: unrecognized option '--case'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:28: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/service/v0 --case underscore --name HTTPClient[/FONT]
[FONT=Verdana]dir: unrecognized option '--case'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:29: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/service/v0 --case underscore --name Publisher[/FONT]
[FONT=Verdana]dir: unrecognized option '--case'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:30: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/service/v0 --case underscore --name Permissions[/FONT]
[FONT=Verdana]dir: unrecognized option '--case'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:31: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/service/v0 --case underscore --name RoleService[/FONT]
[FONT=Verdana]dir: unrecognized option '--case'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:32: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/identity --output pkg/identity/mocks --case underscore --name Backend[/FONT]
[FONT=Verdana]dir: unrecognized option '--output'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:33: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]dir pkg/identity --output pkg/identity/mocks --case underscore --name EducationBackend[/FONT]
[FONT=Verdana]dir: unrecognized option '--output'[/FONT]
[FONT=Verdana]Try 'dir --help' for more information.[/FONT]
[FONT=Verdana]make[1]: [Makefile:34: ci-go-generate] Error 2 (ignored)[/FONT]
[FONT=Verdana]srcpkg github.com/go-ldap/ldap/v3 --case underscore --filename ldapclient.go --name Client[/FONT]
[FONT=Verdana]bash: line 1: srcpkg: command not found[/FONT]
[FONT=Verdana]make[1]: [Makefile:35: ci-go-generate] Error 127 (ignored)[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/graph'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/groups'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/groups'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/idm'[/FONT]
[FONT=Verdana]make[1]: Nothing to be done for 'generate'.[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/idm'[/FONT]
[FONT=Verdana]make[1]: Entering directory '/root/ocis/services/idp'[/FONT]
[FONT=Verdana]pnpm install[/FONT]
[FONT=Verdana]bash: line 1: pnpm: command not found[/FONT]
[FONT=Verdana]make[1]: *** [Makefile:61: node_modules] Error 127[/FONT]
[FONT=Verdana]make[1]: Leaving directory '/root/ocis/services/idp'[/FONT]
[FONT=Verdana]make: *** [Makefile:143: generate] Error 1
```[/FONT]

---

### Post by TheFu on 2023-03-27
Why are you logged in as root?  That isn't how Ubuntu Servers work.  Typically, web-apps run under their own userid or, perhaps, using the web-server userid which is never root.
Doing many things as root on Ubuntu systems is a failure.
So, start over with a fresh install, setup a "deploy" account and do everything under that account, except where sudo escalation is required.

BTW, support for 22.10 ends in June and is not listed as supported by the OCIS documentation, so there's little reason to use any non-LTS release for any production servers ... er ... ever. Go back to 22.04 which is the most recent LTS and **is** listed as supported. [https://doc.owncloud.com/ocis/next/prerequisites/prerequisites.html](https://doc.owncloud.com/ocis/next/prerequisites/prerequisites.html)

Trying to run an unsupported OS isn't worth your time.

---

