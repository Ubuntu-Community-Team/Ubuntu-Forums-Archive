---
title: "Ubuntu Trusts"
date: 2017-12-08
forum: Server Platforms
---

### Post by davyioner on 2017-12-08
[FONT=verdana]Hello, I was wondering if anybody could help me with a configuration I am trying to accomplish. The situation: I have a server running Windows Server 2008 R2, I also have a Server running Ubuntu Server 16.04.3. Both servers are Domain Controllers, windows trough ADDS and Ubuntu trough Samba. I want to configure a Forest trust and Cross forest login, both servers can contact each other and I already configured the trust on the Windows DC. but I am lost on the Ubuntu part. So I was wondering if somebody here has experience with this. I tried to research the subject trough google but there isnt a lot to look trough. I am not asking you to spell it out for me but I would love to have a better idea/direction of where to look. Thanks a bunch and I appreciate your time and help.[/FONT]

---

### Post by darkod on 2017-12-08
Can something like this help you?
[https://www.univention.com/2017/02/creating-trusts-between-ucs-sambaad-and-native-microsoft-active-directory-domains/](https://www.univention.com/2017/02/creating-trusts-between-ucs-sambaad-and-native-microsoft-active-directory-domains/)

I would also investigate the detailed syntax and options/parameters of the 'samba-tool domain' command. It should have a whole subcommand/subsection like 'samba-tool domain trust' that manages trusts.

---

