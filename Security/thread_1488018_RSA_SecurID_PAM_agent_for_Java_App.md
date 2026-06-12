---
title: "RSA SecurID PAM agent for Java App"
date: 2010-05-19
forum: Security
---

### Post by coutoj on 2010-05-19
[FONT=Arial][SIZE=2]Hello All,[/SIZE][/FONT]

[FONT=Arial][SIZE=2]i am working on a project to setup our java based support call tracking software on ubuntu 10.04 server. This is being ported from Suse enterpise server 10.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]I need to setup a PAM agent to communicate with a RSA SercurID server for user authentication. I was able to get it working with the RSA Agent which doesn't use PAM. The software i am using is RSA Authentication Agent 6.0 for PAM [/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www.rsa.com/node.aspx?id=1177[/SIZE][/FONT]]("http://www.rsa.com/node.aspx?id=1177")
 
[FONT=Arial][SIZE=2]the acetest script works (but doesn’t appear to go through PAM)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]My Colleague is trying to use the JPAM 1.1 [/SIZE][/FONT][[FONT=Arial][SIZE=2][COLOR=#0000ff]http://sourceforge.net/projects/jpam[/COLOR][/SIZE][/FONT]]("http://sourceforge.net/projects/jpam")[FONT=Arial][SIZE=2] to use the library from the RSA SecurID PAM agent to make the connection but gets the following error:[/SIZE][/FONT]


 
[FONT=Arial][SIZE=2]SIGSEGV (seg fault) at the following location:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Thread Stack Trace:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at __nss_hosts_lookup+4946()@0x7f3cdea191e2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at _freeConfig+5168(pam_securid.c:1170)@0x7f3c9524ae16[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at pam_sm_authenticate+1819(pam_securid.c:1616)@0x7f3c9524bbc9[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at pam_fail_delay+1005()@0x7f3cdf097f2e[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at iCheckUsersGroup+1181(pam_securid.c:1362)@0x7f3c9524b4ad[/SIZE][/FONT]
[FONT=Arial][SIZE=2]-- Java stack --[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at net/sf/jpam/Pam.authenticate(Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Z)I(Native Method)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at net/sf/jpam/Pam.authenticate(Pam.java:133)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at net/sf/jpam/Pam.authenticateSuccessful(Pam.java:108)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at SecurIDTest.main(SecurIDTest.java:27)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]at jrockit/vm/RNI.c2java(JJJJJ)V(Native Method)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]-- end of trace[/SIZE][/FONT]


[FONT=Arial][SIZE=2]Can anyone help us out.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Jason[/SIZE][/FONT]

---

