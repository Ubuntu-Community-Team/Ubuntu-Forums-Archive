---
title: "Active Directory &amp; Roaming Profiles"
date: 2007-08-03
forum: Server Platforms
---

### Post by nrpgeek on 2007-08-03
I'm new to Linux - I have been using Ubuntu for a couple of weeks now and have successfully set up an Ubuntu machine as an intranet server with LAMP and a couple of Windows network shares using Samba.

I need to go to the next level. There are 10 Networked XP machines, and I want users to log in to the machines with their own username and password and see their own network area, their own desktop, etc. In the future, I'll also need this to work with Vista machines too. It's fairly simple with Windows Server, but I'd really like to move away from Microsoft as much as possible.

Can this be done?
Is it easy or complicated?
Is it well documented?

I've searched through the forums (particularly this one) and the documentation / help section. There are hints that it is possible (LDAP or something like that), but everything seems to be in far too much detail (single detail aspects for someone who's pretty well got it sorted), or nowhere near enough detail.

Any blindingly easy starter guides that I've missed. Google does return results, but for other distros or much earlier versions of Ubuntu.

Many thanks...

---

### Post by koenn on 2007-08-03
how many servers are we talking about ?

---

### Post by nrpgeek on 2007-08-03
Just the one server.

---

### Post by koenn on 2007-08-03
I think for one server + 10 clients, you'd just need  to run SAMBA as Domain Controller on the server, to handle file sharing and authentication, but I'm not sure then how you configure the user accounts so that they are aware that their profile is on a network share to implement roaming profiles.

Active Directory is loosely based on LDAP, but as always MS has added their own features and peculiarities, so I also don't know whether a standard LDAP will be able to implement roaming profiles in a "Windows" kinda way.

---

### Post by Anteaus on 2007-08-03
A key question here is whether roaming profiles are really necessary. On a small network like this, are people going to be playing 'musical chairs' or will they each have their own computer? 

If the latter, then you're just introducing a needless level of complexity, one which will make management of the network a lot more difficult. It will also mean placing draconic constraints on the amount of data users are allowed to amass. (since that data has to be copied to and fro ad inifnitum)

Remember that for fixed desktops you can allocate a 'home folder' on a server where documents are stored by default. This is quite simple to do, and doesn't involve any roaming profiles.

---

### Post by nrpgeek on 2007-08-03
Thanks Koenn...

I've seen some stuff onLDAP and something called Kerberos for validating users against resources - it's looking increasingly possible, but increasingly difficult!

It's probably time to take stock for a while until something precipitates a breakthrough. I've only been using Ubuntu for 3 weeks. I've been using windows nearly 20 years - before that I was at university, playing in a geeky multi user network abled operating system written in C - it was called Unix or something...

I've since forgotten almost all of it :-)

Thanks again good sir!

---

### Post by misconfiguration on 2007-08-03
It is increasingly possible to integrate Linux machines on an Active directory environment. Although OpenLDAP uses the same LDAP protocol, there are other features of Active Directory (including a modified version of Kerberos with a Microsoft specific mechanism called a "PAC") which means that Active Directory clients will not necessarily be able to authenticate against OpenLDAP.

The second limitation of Active Directory is that clients for it (in LDAP mode, that is) are only available on Windows 2000 and Windows XP. Although Active Directory will work in a "down-level" mode to support older Microsoft clients, users of systems such as Windows NT and Windows ME/98/95 who wish to have full LDAP/Kerberos based authentication support are forced to upgrade. 

I have done with with a single 'satellite server' OS was RHEL4, used it to query data from AD to my Linux boxes so AD would actually manage my user accounts instead of me.

It's not an easy task to complete, some think just strictly using OpenLDAP in place of AD could be easier, I hope some of this made sense, good luck to you!

---

### Post by nrpgeek on 2007-08-03
Hi Anteaus...

Many thanks for the repy

Yes - each user will need their own ID and associated 'network area' (sorry if that's micro$oft speak) at the least. Having the desktop, favourites, etc follow them round would be a real bonus - both for the users (learners & clients) and administratively.

This is the reason I'm playing with Ubuntu.

We now need a server, instead of the informal peer to peer stuff at present - the organisation has had to evolve. We are in the process of specifying new machines, and I don't have the final say in that.

The organisation either pays for Window$ $erver and doubtless lots of licences for Vista, or I get this working in Ubuntu (along with a few desktop machines with Ubuntu & Kubuntu). If I can show them something that works and saves them money they'll take that direction (there will still have to be a few windows machines unfortunately).

I've had six months of Vista now and I don't like it, I genuinely believe that the future is not going to be Microsoft for long. Vista is expensive software, requires expensive hardware for no substantial improvements at all.

---

### Post by koenn on 2007-08-03
> **misconfiguration said:**
> It is increasingly possible to integrate Linux machines on an Active directory environment ... 
quite true, but that assumes there is an AD domain, to which you can join a samba server that holds the home and profile folders. But telling the clients where there home and profile is located, is still done from AD, and authentication is managed by AD as well. 
It is possible to use standard LDAP and Kerberos, runnin on Linux,  for authentication and authorisation of Windows (2k, XP ...) clients but you still need the centralised configuration features, eg to implement roaming profiles. Unless LDAP has an attribute for "profiledir" or something. 

A possible workaround could be to keep the profiles on the server and "manually" copy them over to the Documents and Settings folders   via a command in the login script. Tricky, and local changes wouldn't go back to the server. 

An other workaround could be to map a driveletter to a share on the samba server, and point  the ProfileDIr registry key on the clients to that drive. Might work. 

Before you even consider that, you'd probably have to think whether you really need roaming profiles. If users can login to any machine, and all machines are (almost) identical, you can have free seeting without the need for romaing profiles, provided that their personal files are in a home directory on the server.  Keeps it simple, and gives you a change to get used to Linux in a mixed environment.

---

### Post by nrpgeek on 2007-08-03
Ah...

Thanks for that Misconfiguration.

The networked machines are all XP and win2000. All I need then is OpenLDAP and Samba?

Many thanks again...

---

### Post by nrpgeek on 2007-08-03
This is all good stuff folks, thanks all for your help...

Roaming profiles would be really desirable, but are increasingly looking like a pain in the bum. Using Samba itself isn't too difficult, but the rest looks very daunting with my lack of experience.

I can give users login IDs and network shares on the server - not bad for a Linux novice and it's 75% of the battle with a few workarounds as suggested.

All in good time perhaps - when I've built up a level of experience over months rather than weeks - I'm going to sleep on this after a beer with the lads maybe!

You all deserve one too :-)

Thanks again...

---

### Post by koenn on 2007-08-03
> **nrpgeek said:**
> H ...  or I get this working in Ubuntu (along with a few desktop machines with Ubuntu & Kubuntu).
That would be far easier. As you know, anything user-specific is in /home/user_name, so having these on a server, exporting them (NFS, SAMBA), and mounting them locally effectively makes for roaming profiles. If only it was that easy on Windows clients as well. 

What exactly do you mean by "network area" ?

---

### Post by koenn on 2007-08-03
hmmmm, beer ...

---

### Post by Anteaus on 2007-08-08
> **koenn said:**
> That would be far easier. As you know, anything user-specific is in /home/user_name, so having these on a server, exporting them (NFS, SAMBA), and mounting them locally effectively makes for roaming profiles. 

Was discussing this on the MS forums a while back, and the lowdown seems to be that Windows does have the capability to relocate "Documents and Settings" - the profile root- but that doing so is 'unsupported.' I guess that's a roundabout way of saying that it may work, but if it breaks, you get to keep both pieces. 

The other point to watch is that two main MS email clients (Outlook/Express) store their local data in folders which do not roam, thus having roaming profiles does NOT automatically give you any-user email. To achieve this you either need to relocate the mailstores, or else install an Exchange server (another wad of $$$$'s, and another head-banging session getting it to work!)

Thunderbird, OTOH, works very nicely with the mailstore in a server home-folder. Since TBird's settings are in the mailstore as well as the messages, it's an ideal network-based program, change mailstore and not only the visible messages but also the user's ID changes in unison. Plus, it has a Linux counterpart.

---

### Post by wjlroe on 2007-08-14
> **Anteaus said:**
> The other point to watch is that two main MS email clients (Outlook/Express) store their local data in folders which do not roam, thus having roaming profiles does NOT automatically give you any-user email. To achieve this you either need to relocate the mailstores, or else install an Exchange server (another wad of $$$$'s, and another head-banging session getting it to work!)


In my experience, Outlook does roam. It stores it's data in Local settings in the user's Documents and Settings folder (which is part of the [roaming] profile). For POP mail it uses a PST which can be stored anywhere (network or local).

---

### Post by netlogic on 2007-08-14
If you need AD, you are better of using AD. Trust me. If your need is very simple for home and small office, use Samba. It takes few minutes to setup a Samba DC. Remember, Samba only works for one location. If your company grows, and clients are Windows, just get AD and make sure you set 2000/20003 AD as Mixed mode. You can't connect Samba DC through Native Mode AD. Once, you set your MS AD to Native, you can't go back to the mixed mode. You can also switch Samba DC to Samba standalone server make it join AD. Trying to password sync all the accounts through multiple separate SAMBA domains isn't worth your time. 

1. One site with a mixed environment, Samba. 
2. Multiple sites with all Unix machines, try different form of non-MS LDAP. 
3. Multiple sites with a mixed environment, just use MS-AD. Even commercial Linux servers aren't fully ready replace everything MS YET.

The roaming profiles with Samba is broken, because it will not properly sync as the size of the profile grows. Samba handles it like a file transfer. I would avoid that feature. I would recommend using Rsync for windows or Unison to sync configurations during logoff or logon such as Outlook, Desktop configs, bookmarks and other Application Data configs that need to be synced.

I use both platforms for home and work. Linux isn't better for everything. It is always best to weight the pros and cons for both platforms.

---

### Post by netlogic on 2007-08-14
Oh, I forgot how large Outlook pst file can get. I am going to make an assumption, you are not using any server end to sync and streamline your groupware features in Outlook. It is only being used as a pop3 reader and personal scheduling. It isn't hard to write VB variables to turn on timing variables when users logon. You can search the google for example scripts. You can set it up, so after four minutes of logon on session, start a backup copy (free version robotcopy is good for windows) in a lower priority. Ms has a command called, start which can work like nice. That way, client machines don't have to wait for batch scripts to complete before they start working.

---

### Post by HermanAB on 2007-08-14
This may help to get you started:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

It discusses doing it the other way, with a MS Server, but the comments on Kerberos are largely applicable.  Anyway, the more you know about this problem, the better, so this guide will help some.

---

