---
title: "server.js:204 LDAP &#10132; Connection.error connection time out 1000  + Ldapjs"
date: 2021-02-04
forum: Server Platforms
---

### Post by codingsource21 on 2021-02-04
Hi , i have openLDAP installed on an ubuntu 16.04 server.  Everything works fine unti lmy site becomes inaccesable. I am running rocketchat with openLDAP , after a while my site becomes 
```
[This page isn’t working domain.com didn’t send any data. ERR_EMPTY_RESPONSE]("https://forums.rocket.chat/t/this-page-isn-t-working-domain-com-didn-t-send-any-data-err-empty-response/10167")
```

Now debugging the issue i see that on error log i can see this :

 ```
[COLOR=var(--black-800)][FONT=Consolas]server.js:204 LDAP &#10132; Connection.error connection time out 1000[/FONT][/COLOR]Feb 04 10:46:01  rocketchat-server.rocketchat-server[3374]: server.js:204 LDAPSync &#10132; error Error: Timeout
Feb 04 10:46:01  rocketchat-server.rocketchat-server[3374]:     at Timeout._onTimeout (app/ldap/server/ldap.js:181:14)
Feb 04 10:46:01  rocketchat-server.rocketchat-server[3374]:     at listOnTimeout (internal/timers.js:549:17) [COLOR=var(--black-800)][FONT=Consolas]Feb 04 10:46:01  rocketchat-server.rocketchat-server[3374]:     at processTimers (internal/timers.js:492:7)[/FONT][/COLOR]
```

The service status is active but the site is inaccesable . Before the error above the console shows this :

```
[FONT=Helvetica]Feb 04 13:44:11 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“101__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:11.860Z”,“v”:0}[/FONT][FONT=Helvetica]Feb 04 13:44:13 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“102__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:13.084Z”,“v”:0}[/FONT]
[FONT=Helvetica]Feb 04 13:44:14 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“103__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:14.303Z”,“v”:0}[/FONT]
[FONT=Helvetica]Feb 04 13:44:15 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“104__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:15.509Z”,“v”:0}
Feb 04 13:44:16 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“105__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:16.716Z”,“v”:0}[/FONT]
[FONT=Helvetica]Feb 04 13:44:17 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“106__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:17.933Z”,“v”:0}[/FONT]
[FONT=Helvetica]Feb 04 13:44:19 aaa rocketchat-server.rocketchat-server[31062]: {“name”:“ldapjs”,“component”:“client”,“hostname”:“aaa”,“pid”:31141,“clazz”:“Client”,“ldap_id”:“107__ldap://IP”,“level”:20,“msg”:“connected after 1 attempt(s)”,“time”:“2021-02-04T13:44:19.141Z”,“v”:0}[/FONT]
```

I am pretty new with LDAP and i cant seem to identify the issue . Any help is appreciated.

---

