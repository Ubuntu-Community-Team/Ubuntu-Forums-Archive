---
title: "Windows SBS replacement"
date: 2009-10-03
forum: Server Platforms
---

### Post by xandout on 2009-10-03
I work at a local PC repair place and my boss is from the server world (i am not) and he wants to expand this business into the server arena.  He said that this area just cant afford MS server licenses and asked about linux.  He needs the server to be linux but the clients could be XP Pro and it needs mail, DNS/DHCP, file, print, and what i believe he called group policy (a way to control what clients can and cannot do on their pc's and what they can access on the servers?).   I can only imagine that the linux needs to be transparent as far as the users go.   I've looked at Xandros and RHEL and for the cost windows would be fine.  Is this possible?

Thanks ahead

---

### Post by hessiess on 2009-10-03
Samba could do some of those things.

---

### Post by Lem on 2009-10-03
Have a look at the ebox platform, or running a plain Ubuntu Server with Webmin - This would be the easiest for a Windows Server user. The only point I could see is there is not a linux equivalent to Group Policy as far as I'm aware

---

### Post by xandout on 2009-10-04
i found a few pay options Centrify and Nitrobit.  Does samba allow linux to be hidden with no special tweaks for windows?  Thanks for the replys.

---

### Post by BadBoy4Live on 2009-10-04
> **xandout said:**
> I work at a local PC repair place and my boss is from the server world (i am not) and he wants to expand this business into the server arena.  He said that this area just cant afford MS server licenses and asked about linux.  He needs the server to be linux but the clients could be XP Pro and it needs mail, DNS/DHCP, file, print, and what i believe he called group policy (a way to control what clients can and cannot do on their pc's and what they can access on the servers?).   I can only imagine that the linux needs to be transparent as far as the users go.   I've looked at Xandros and RHEL and for the cost windows would be fine.  Is this possible?

Thanks ahead

Authentication for windows: LDAP
[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

As for the Mail server, There are a lot of options like: citadel, postfix, sendmail. Just know that wichever you choose, its going to require a couple of ours to get it to work.
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

The DNS Server can be made with Bind
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

The DHCP Server with DHCP3-Server
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

File Server with Samba
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Printserver with Cups
[https://help.ubuntu.com/8.04/serverguide/C/cups.html](https://help.ubuntu.com/8.04/serverguide/C/cups.html)

As far as i know, Linux does not support GPO(Group Policy Objects), but correct me if i'm wrong

I Think you ment to ask if you can use samba without modifying windows, the answer to this is yes. Samba simply allows you to share folders, nothing else.

Hope it helps
Badboy4live

---

### Post by brettg on 2009-10-04
You could take a look at novell eDirectory, which used to be called Novell Directory Services (I think) and was what MS originally copied for AD

---

### Post by bab1 on 2009-10-05
You mght try [**_this_**]("http://directory.fedoraproject.org/") as a subtitute for MS AD.  Novel is as expensive a Microsoft and most other LDAP solutions don't have all of the features of MS AD.

---

### Post by brettg on 2009-10-05
Thanks for the link bab, I'm going to check that out myself

---

### Post by lykwydchykyn on 2009-10-05
> **brettg said:**
> You could take a look at novell eDirectory, which used to be called Novell Directory Services (I think) and was what MS originally copied for AD

We use eDirectory where I work; supposedly it does group policies, but we've never tried this feature.

In all other respects, it offers most of what is needed -- file/print/email/calendar/dns/dhcp/etc.  However, it's NOT click'n'go (you need to learn a good bit of terminology and understand what you're doing) and I don't honestly know how the pricing compares.

IMHO (and experience) group policies are a bit over rated.  I can imagine it sounds very tempting to someone who is tasked with keeping employees productive and computers operating, but too often I've found that locking down a machine only comes back to bite me.  Very often restrictions have unintended side effects, and finding the one you need in a given circumstance can be tedious (at least it was on server 2k3, maybe 2k8 has fixed that, IDK).  

I'm not saying there aren't situations where it's useful, or taking a "Linux can't  do it so you don't need it" stance.  Just saying, it's a lot better in theory than in practice, and I wouldn't write off an inexpensive alternative just because I couldn't do it.

---

### Post by sunstriker on 2009-10-05
You can use Zimbra + Samba for MS Exchange replacement (important feature of SBS). With some tweaking, it can play for AD server (File sharing, authenticating clients) However, I don't believe you can find a replacement of group policies (but small businesses don't need them most of the time)

---

