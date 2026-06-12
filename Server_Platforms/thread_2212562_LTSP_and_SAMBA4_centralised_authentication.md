---
title: "LTSP and SAMBA4 centralised authentication"
date: 2014-03-21
forum: Server Platforms
---

### Post by victor22 on 2014-03-21
Hi there,

I am just wondering if there is a way I can authenticate users with Samba4 inorder to log in to LTSP clients? I have searched on the internet everything seems really hard to understand. Any tips would be helpful cheers.

---

### Post by houstonbofh on 2014-03-23
Yes, but why?  You are going back and forth through many layers of translation here.

What are you using on the samba server for authentication?  (LDAP?  PAM?  MS Active Directory?)  Now, use that directly for the LTSP clients.

---

### Post by victor22 on 2014-03-24
Hi thanks for the reply, I installed likewise open on my ltsp server, I could join the domain and login. However when i try to login on my ltsp client it doesn't work just says could not contact server. Could it be that i have set up dhcp for LTSP clients on a different network adapter and maybe it has problems resolving the samba4 server?

---

### Post by houstonbofh on 2014-03-26
Ick...  I am the one that "fixed" the community documentation on Likewise Open, PBIS...  And it is not exactly clean.  So troubleshooting this will be a challenge.  You will have to go through each system and make sure it is pointed to AD auth...  You may have to specify the AD server in a lot of places.

---

### Post by lingpanda on 2014-03-26
Is the DHCP server setup to point to your Samba4 server for it's DNS? I assume you are using the internal DNS server for Samba? Did you enable the other login option on Ubuntu?

---

### Post by victor22 on 2014-04-02
Hey mate, 

Sorry it took a while to reply but so far its all working... all I had to do was run the lwconfig AssumeDefaultDomain true command and it works. So now I can log into LTSP clients using AD credentials cheers. One problem I am having now is that instead of having Samba4 and LTSP on separate servers, I want to have them both on 1 server.. The problem now is when I try to use likewise to join the samba4 server to it self it gives an error. Or is this approach just not practical? Because if I install the ltsp on my Samba4 AD DC server how will it access AD users without Likewise? I guess i need to find another way to access AD user credentials, I am having a look at the Samba4 wiki methods but they are very hard for me to understand.

---

### Post by victor22 on 2014-04-05
update: I have tried Zentyal which has the ability to allow domain users to be logged in via SSH and Bash. I tried to install LTSP on top of it but it doesnt seem to work at the moment. 
I have also tried [https://wiki.samba.org/index.php/Samba4/Winbind](https://wiki.samba.org/index.php/Samba4/Winbind) it works to the point where it asks to edit the pam.d/common files then I cant log into my system at all.**&#8203;**

---

### Post by Neeeeds on 2014-05-08
Hello mate, can you tell me more about how you did the ltsp-samba4 system thank you very much.

---

### Post by victor22 on 2014-05-09
Hey its been awhile but im going to share my results.. I have managed to retrieve AD users to the local machine using either winbind/pam or Lbnssldap nslcd and trying nssd. I am still having trouble configuring those local users to be able to use ltsp clients. However instead I am now using samba 3 with openldap as centralised authencation and it works perfectly with LTSP. cheers.

---

