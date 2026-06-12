---
title: "Basic user-authentication server recommendations?"
date: 2007-07-04
forum: Server Platforms
---

### Post by BroadArrow on 2007-07-04
I'm after a recommendation for a basic user-authentication server for a home network.

I'm after something simple so family members (and perhaps a guest account) can log on to an Ubuntu workstation and have their log in authenticated (and perhaps /home folders stored) on an Ubuntu server on the local (wireless) network.

I found the [LDAP server HOWTO]("https://help.ubuntu.com/7.04/server/C/openldap-server.html") but it doesn't simply explain how to do this and might not be the best option. Maybe there's another FAQ out there that does explain how to do it, perhaps also explaining how to set up a NFS share for a uer's home folder as well?

Are there any other recommended solutions?

---

### Post by kidders on 2007-07-13
Hi there,

I have to say I've found LDAP-based solutions quite satisfactory, not least because they're reasonably platform-independent.

---

### Post by BroadArrow on 2007-07-14
> **kidders said:**
> I have to say I've found LDAP-based solutions quite satisfactory, not least because they're reasonably platform-independent.

Thanks for the response -- although it was the answer that I feared because I haven't found any user-friendly HOWTO for setting up an LDAP server for a small home LAN. I'll have to have another look around for one...

---

### Post by kidders on 2007-07-14
Yeah... while I was typing my last post, I was conscious that I was probably typing exactly what you *didn't* want to read hehe! Getting OpenLDAP, for example, properly configured has never (at least for *me*) been particularly straightforward ... especially if I want to create something that can act as a Microsoft domain controller. Unfortunately, it gives pretty good results though! Linux, Windows, OS X and others can all authenticate against LDAP servers, and many applications (eg mail clients & address books) can also make good use of the user database.

In a Linux only environment, NFS (as you mentioned) is the way to go for profile storage. The usual practice is to pull client computers' entire /home directories off a file server, so that all user-specific data is stored centrally. On multi-OS networks, Samba and/or AFP can be used to achieve a similar effect.

I would very strongly recommend saving things like Samba or OpenLDAP configuration files on a USB disk or a CD, once your done with them. That way, you'll only ever have to go through the setup process once. Even if you were to format your server and install a completely different Linux distro on it, you could use the saved config files to set your user authentication & profile management back up in 90 seconds flat.

Another piece of advice I should probably add is that (from experience) I've found that many HOWTOs on this subject contain minor errors/oversights. It might be worth trying to find two good guides (rather than just one), and sort of "blending" them together.

Question: What kinds of OSs would you like to plug into your authentication server? (I may be able to suggest some good search keywords for you.)

---

### Post by Mr. C. on 2007-07-14
Am I safe in presuming that your home user's are Windows users?  If so, just setup your Ubuntu server as a Samba domain controller, and configure the workstations as members of the domain.  You don't need LDAP for that, and you'll have login / password control via the Samba PDC.

MrC

---

### Post by BroadArrow on 2007-07-16
> **kidders said:**
> Question: What kinds of OSs would you like to plug into your authentication server? (I may be able to suggest some good search keywords for you.)

I'm hoping to move to a Linux-free environment but have a couple of 'legacy' Windows machines: a media centre PC running Windows XP MCE and my wife's work laptop running Windows XP. Everything else in the house is Ubuntu.

---

### Post by Mr. C. on 2007-07-16
"Linux-free"  <> "free Linux" !  ;-)


MrC

---

### Post by kidders on 2007-07-16
Hmm...

In that case, I would probably go the Samba PDC route. As Mr. C. said, that *can* be done without an LDAP service, but I've never tried it that way in a mixed OS environment, personally.

Samba's Windows domain management is very nice (although getting it to work 100% perfectly can be a bit finicky, first time out). I would ...[LIST]
[*]Set Samba up to authenticate against an LDAP server.
[*]Have it expose user profiles which, ideally, should be kept out of /home.
[*]Set up a [homes] share, for personal filestorage.
[*]Have each of the Ubuntu boxes authenticate against LDAP directly.
[*]Expose the whole of the server's /home over NFS, so client machines can mount it.[/LIST]There's a range of tools available for Windows and Linux that you can use to manipulate LDAP databases, so you can add & remove users easily. If you prefer, there are also one or two web-based ones.

I'm interested to hear what Mr. C. would set up though. Hehe.

---

### Post by Mr. C. on 2007-07-16
At home where we have only a few systems, I find a management server to be more headache than its worth.  For our Windows XP Pro machines, I setup the same user accounts and passwords on each machine, so that Windows file and print shares are functional like they would be with a PDC/Active Directory.

With more than a few systems, an authentication server is useful, especially when there are users who need access controls (we don't have that as a concern - no little ones running around).

We also don't use mapped home directories, since we each have our own systems, and don't often use each other's.  But again, and a larger environment, this is a very handy feature.  I can see where with a family of 5 or more, plus their friends, guests, etc. the ability to log into any machine on the home net would be very nice.

I have considered setting up a home LDAP server for our personal access, and perhaps some remote access for others; but for us, this is just a solution looking for a problem, and hasn't been worth the trouble.

An office environment is an entirely different story.  There, much more control is required, and central control is a time saver.

Anyway, just a little rambling,
MrC

---

### Post by kidders on 2007-07-16
Worthwhile ramble! :-)

"Don't" may seem like a strange answer to "How should I set up centralised authentication", but ...

I have to say, I certainly see your point. I very often find myself going to the trouble of implementing the technically elegant, scalable approach to something, simply because it seems like the "correct" thing to do ... not necessarily the most practical. In this case, if the number of computers involved is very small, simply deciding not to bother would be *waaaay* less hassle.

I guess it's up to BroadArrow to decide what road he'd like to go down. :-)

---

