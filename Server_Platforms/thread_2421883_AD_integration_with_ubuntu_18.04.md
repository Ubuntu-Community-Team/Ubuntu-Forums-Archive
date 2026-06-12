---
title: "AD integration with ubuntu 18.04"
date: 2019-06-28
forum: Server Platforms
---

### Post by sjefke on 2019-06-28
Hi all,

I got a set of questions i don't seem to find on the internet and i was wondering if anybody can help me answer these.
My boss wanted me to set up a VPN server, the DevOps and security team told me a Ubuntu server is better for VPN services than windows, and they also wanted that we could use our AD accounts on the Ubuntu server.

We are running all our servers in Azure and i got there 2 Windows 2016 servers for redundancy with the AD role installed, we do not run any apps on those servers just 2 DC's with the AD role installed. it is just 1 single domain i have running on the servers and no shares on it, people just want to use VPN services for remote tasks from home and maybe run my hybrid cloud print server over that VPN. (our users all use office 365, for data we use SharePoint/one drive etc so no need for shares on a server)

I'm looking through the documentations from Ubuntu and i found out Samba is being used to integrate the AD from windows with Linux to say it this bluntly.
(i run myself at home a Ubuntu machine for a year and i love it, i know the more than the basics in the terminal and i also develop on that with Python, i run a windows VM to test some Powershell scripts if i really need to and i know Windows servers good enough, I don't have any issues configuring those machines and it always worked flawlessly for me. (This is the first time setting up a Ubuntu server with a real "purpose" i toyed in the past with Ubuntu servers in VM's just to get a taste of it but i'm not a pro - like i mentioned i always worked with windows server)

However a few things are bit unclear for me, for starters there is SSSD and winbind, and there is LDAP and Kerberos. (I see all the people recommend SSSD over winbind)
The other thing is when i look at the diagrams from a redhat information page about all the different methods of authenticating between windows and Ubuntu server is that they write down LDAP/Kerberos. (can i either use one of the 2 or do i need to install both?) [https://www.redhat.com/en/blog/overview-direct-integration-options](https://www.redhat.com/en/blog/overview-direct-integration-options) in the diagrams it states: authentication can use LDAP, kerberos or NTLM. ( so i guess i can choose which one?)

I don't run any Windows server at the moment with the LDAP role installed and i was wondering if only 1 of the 2 servers need the authentication method set up (I know stupid question but i don't find an clear answer only that LDAP and kerberos are a great combination)

Second question is ( i think i may be wrong on this forum for this) Is it wise to run on both of my Dc's LDAP role to authenticate between Kerberos and LDAP?
My security officer goes insane if i screw up by not securing the authentication between the servers.

I did a test setup and i did not set up LDAP on a windows server but i did set up Kerberos with winbind, (i could login with my useraccount and admin account) but then i thought that the authentication part is not correctly set up and i wanted to know from you guys what you recommend, what i should read/study in order to solve my problems.

thanks for your time and help!
best wishes,

Sjef

---

