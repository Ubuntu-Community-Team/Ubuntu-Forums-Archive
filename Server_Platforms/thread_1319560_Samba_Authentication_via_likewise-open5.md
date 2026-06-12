---
title: "Samba Authentication via likewise-open5"
date: 2009-11-08
forum: Server Platforms
---

### Post by robgolding63 on 2009-11-08
Hi,

I have an Ubuntu Desktop machine, which is used as a sort of terminal server (using VNC). It is joined to my Windows AD Domain, and I wish to set up a samba share on the machine, which will use AD for authentication.

I have found some how-to's and tutorials on this matter, but they all seem to be referring to either old versions of Samba, or the version of likewise that is in the "likewise-open" package (not likewise-open5). I know there have been major changes made in this new version (lsass now used, instead of winbind etc.) - so the articles don't really apply to this situation.

I did have a try, just to see if it was already working "out-of-the-box", but it just kept asking me to re-authenticate as if my credentials were incorrect.

Does anyone have experience with this?

Thanks in advance :)

Rob

---

### Post by trinaryouroboros on 2009-11-18
> **robgolding63 said:**
> Hi,

I have an Ubuntu Desktop machine, which is used as a sort of terminal server (using VNC). It is joined to my Windows AD Domain, and I wish to set up a samba share on the machine, which will use AD for authentication.

I have found some how-to's and tutorials on this matter, but they all seem to be referring to either old versions of Samba, or the version of likewise that is in the "likewise-open" package (not likewise-open5). I know there have been major changes made in this new version (lsass now used, instead of winbind etc.) - so the articles don't really apply to this situation.

I did have a try, just to see if it was already working "out-of-the-box", but it just kept asking me to re-authenticate as if my credentials were incorrect.

Does anyone have experience with this?

Thanks in advance :)

Rob

I just got off the phone with Likewise Open support team, **the Ubuntu Repositories for 9.10 came with packages that were over Eight Months old**, there's many module bug fixes that have occurred in the past year for the likewise-open5 software, and it was recommended to me to perform the following to ensure smooth operations with the latest version:

[COLOR="Red"]Step 1: Leave the domain if currently joined

Step 2: Uninstall old one completely (you can use synaptic and do a Complete Removal, or just `sudo apt-get remove likewise-open5`

Step 3: Remove all files in `/var/lib/likewise/db/`

Step 4: Download Latest Likewise Open 5.3.7709 - and use their instructions on the site to install it properly. 

(IMPORTANT: They state, while you go through the Likewise Integration Guide, after the major step # 6 (around page 8 or 9), you must Redo winbind Restart command.  So even though you Just restarted winbind...after that step you must Do it Again!)
[/COLOR]
That should do it, let me know your success, I've been burning brain synapses for a few days on my own likewise-open5 trouble, thanks to a no good package on Ubuntu's repo, but, that's life.

](*,)

Man, I'm gonna have to go to the dentist after all this teeth gnashing.

P.S. - you may also have to move "/etc/samba/secret.tdb" to secret.tdb.orig or such, as that's the Samba cache

---

### Post by robgolding63 on 2009-11-20
Oh right, I guess that's a pretty common problem - old packages :).

I'll give it a go and see what happens.

Cheers for letting me know about the phone call!

Rob

---

### Post by trinaryouroboros on 2009-11-25
> **robgolding63 said:**
> Oh right, I guess that's a pretty common problem - old packages :).

I'll give it a go and see what happens.

Cheers for letting me know about the phone call!

Rob

I just wanted to say, that albeit there was a slight post-warning, we've been live with fully blown integrated Samba 3.4 & Likewise Open 5, using the new .DEB package from the Likewise Open web site.

I can SSH to it using 'DOMAIN\username'@myhost, plus, from a Windows machine, regardless of architecture, I can log into Windows as a Domain User, and simply do a "net use F: \\sambahost\share" or even a Start>Run "explorer \\sambahost\share" - and with Samba's smb.conf handling all the permissions, the user literally gets Right into that File Share, password only at Windows login, and that's it! 

SSO for the win!

I'll be intermittently checking my email for any follow ups to this forum, if you need a hand just let me know.

:guitar:

---

### Post by damageboy on 2009-12-07
> **trinaryouroboros said:**
> I just wanted to say, that albeit there was a slight post-warning, we've been live with fully blown integrated Samba 3.4 & Likewise Open 5, using the new .DEB package from the Likewise Open web site.

I can SSH to it using 'DOMAIN\username'@myhost, plus, from a Windows machine, regardless of architecture, I can log into Windows as a Domain User, and simply do a "net use F: \\sambahost\share" or even a Start>Run "explorer \\sambahost\share" - and with Samba's smb.conf handling all the permissions, the user literally gets Right into that File Share, password only at Windows login, and that's it! 

SSO for the win!

I'll be intermittently checking my email for any follow ups to this forum, if you need a hand just let me know.

:guitar:

Did you have to do anything to get samba to authenticate with SSO?
I've just installed likewise-open 5.3 on a Karmic machine, but didn't have samba installed at the time.
Does this mean I have to leave the domain, install samba, and then re-install likewise?

I do have likewise working properly right now, even using a specialized putty version that supports gssapi for SSO using putty to my ubuntu machines.
The only thing I'm missing is SSO for samba.

What document are you referring to for installation?

---

### Post by damageboy on 2009-12-07
Found what I was looking for:

[http://likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf]("http://likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf")

---

### Post by trinaryouroboros on 2009-12-09
> **damageboy said:**
> Found what I was looking for:

[http://likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf]("http://likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf")

:-k

**I've been working with support for over a week now, there's several problems here:**

First and foremost, the machine account loses it's password with Samba 3.4 - Likewise only supports up to Samba 3.2 - there was a huge change that prevented their development with Samba further.  At that juncture, they decided to focus more on their own File Server than Samba.  In fact, it is purportedly going to rock, called "Likewise-CIFS" or "LCIFS" - it's due out with the next release of Likewise Open 5.4 sometime next month.

**In the meantime, I have removed Samba 3.4, and by searching Ubuntu's repositories web site I discovered a good and still working package of Samba 3.2 for Intrepid Ibex's repo.**

After downloading the .deb packages and installing Samba 3.2, I followed the procedure as outlined by the Likewise Open 5 / Samba 3.2 integration document, and successfully set up full SSO without losing the machine account authentication the following day.

So far I've been able to test connections via Windows Machines, and Nautilus "Connect to Server" in Gnome, without a hitch.

\\:D/

**Note: If you're going to do this yourself, I highly suggest you do a couple of things afterwards, to ensure the Samba 3.2 packages don't get updated to 3.4:**

```
sudo aptitude
```

In there, find the samba packages, and on top you can click on one of the menus in the upper left, which will give you an option to Hold the Package.

Or, you could just do:

```
sudo aptitude hold package_name
```

Secondly, just for security sake, open Synaptic (X / Gnome only):

```
gksudo synaptic&
```

From here, you can find the samba packages, and on top click Package > Hold Package, or something equivalent, to put a stop in Synaptic as well.

**There are still three problems, in general, to resolve:**

:arrow:[INDENT]1) Windows Server 2008 x64 edition: 

[INDENT]We have this set up as a Terminal Server, and for some reason it's not able to use the Samba File Server like the Server 2003 machines.  On Windows Server 2003, and XP, the domain authentication takes care of everything and we can do either a "explorer.exe \\fileserver\sharename", or "net use X: \\fileserver\sharename" without needing to type a password - however, on Windows Server 2008 x64 specifically, for some reason, the authentication process dies.  

What happens is, if you use the explorer.exe method, it fails to connect and presents either a "Diagnose this problem" message, producing a useless system event in the event viewer, or, it asks you to login - but even with DOMAIN\username, and password, it fails anyway with the "Diagnose this" problem. 

The second method, doing "net use", asks immediately for a username/password, and even with domain credentials it fails with "System Error 5" or something equivalent like "System error 68" - Likewise Open support has this one specific bug under investigation currently, after I conducted a few tests with Wireshark, but, I could technically work around it by using another Windows server as a launchpad if needs be.[/INDENT][/INDENT]

:arrow:[INDENT]2) Linux Share Mapping:

[INDENT]Albeit Nautilus is gnarly, in opening right up to the share by using the "Connect to..." feature in Gnome under Ubuntu or other linux distributions, it doesn't make it easy to Browse to that as a directory/mount.

I.E., let's say you wanted to use Thunderbird, and send an attachment via email off that share - can't be done, because the file system has no idea what that share is, and this share is purely being maintained and managed by Nautilus itself.

There is a fix for this, the question that one poses is:  

**If domain passwords are changing and such, how exactly can I mount the share when the user logs into Gnome?** 

Fortunately, for Ubuntu users, there's a way to do this using pam_mount - and there's a few guides if you merely Google "Ubuntu pam_mount user session" or the like, and it purely involves setting up pam_mount properly, and dropping a little hidden xml config file in the users home directory - however, my new problem is with Fedora Core linux, version 10 through 12.

](*,)

The Fedora desktops don't behave appropriately with pam_mount, and there's little in the way of help online. I've been researching it for days without getting it working, but, basically when a user logs in, I can get it so pam_mount shows the network share as a "removable drive" under Places in Gnome...but, it doesn't work, and complains about the password for some reason. At any rate, that is something else that's in the mix, and perhaps hopefully will be fixed with the new L-CIFS file server Likewise is rolling out next month...[/INDENT][/INDENT]

:arrow:[INDENT]3) Mac OS X Share Mapping: 

[INDENT]Mac OS X has a Directory Access utility, of which interferes with simple network file share mapping via Likewise.  There's also some unusual permissions behavior that occurs, which causes a bit of mischief with how things get saved on that file share (provided you use manual share mapping instead of the environment). [/INDENT][/INDENT]

**What I'm concluding to is the following, sadly:**

It's either that Likewise's new baby, L-CIFS, will be the answer to all our problems, or, we'll be stuck doing manual file server mapping with a Windows server, and let the Windows server handle all the domain mapping - allowing other programs to directly interact with it.

:neutral:

I'm really going Against the latter case here, but we'll see what happens.

Sorry I couldn't get back in touch with you fast enough, in regards to the manual information.

---

### Post by trinaryouroboros on 2009-12-09
> **damageboy said:**
> Did you have to do anything to get samba to authenticate with SSO?
I've just installed likewise-open 5.3 on a Karmic machine, but didn't have samba installed at the time.
Does this mean I have to leave the domain, install samba, and then re-install likewise?

I do have likewise working properly right now, even using a specialized putty version that supports gssapi for SSO using putty to my ubuntu machines.
The only thing I'm missing is SSO for samba.

What document are you referring to for installation?

Almost missed the middle question here, YES: You need to actually Leave the domain entirely, uninstall Likewise 5, install Samba, then install Likewise 5, join to the domain, and continue their set up.

**Additional hints, this will help you Big Time:**

```
sudo nano /etc/likewise/lsassd.conf
```

This file contains a few things, like the Default shell for authenticated users (I change this right to /bin/bash myself) and "Assume-Default-domain", which makes it so you purely have to just type the users name instead of the DOMAIN\user to log in (note, changing this won't affect any Current profiles, you will still use that same profile when logging in without the domain prefix) - also, importantly: 

**There's an authentication measure that's not being conducted by default.** Check your authentication in this file, look for a section regarding the secrets.tdb file - by default with the SQL config, this section is commented out, which causes winbind to have No idea what's going on! So uncomment this /etc/samba/secrets.tdb section of that file!

---

### Post by chaggie on 2009-12-21
Could you tell me how you installed samba 3.2 on Karmic?
I added a Intrepid repo so that I can install 3.2 samba but I am getting an error with samba-common. 

Thanks.

---

### Post by trinaryouroboros on 2009-12-27
> **chaggie said:**
> Could you tell me how you installed samba 3.2 on Karmic?
I added a Intrepid repo so that I can install 3.2 samba but I am getting an error with samba-common. 

Thanks.


The correct repo is Intrepid, what is the error?

---

### Post by Zeon100 on 2010-01-17
Has anyone tried the built in CIFS server on Likewise Open IE you don't even need Samba anymore?

---

### Post by robgolding63 on 2010-01-17
> **Zeon100 said:**
> Has anyone tried the built in CIFS server on Likewise Open IE you don't even need Samba anymore?

Yeah I gave it a try, but I didn't like the fact that you have to manage It from a windows machine. I'm now using winbind RID mapping to make sure the UIDs are always the same throughout the network, and of course it integrates perfectly with Samba!

Rob

---

### Post by trinaryouroboros on 2010-01-23
> **robgolding63 said:**
> Yeah I gave it a try, but I didn't like the fact that you have to manage It from a windows machine. I'm now using winbind RID mapping to make sure the UIDs are always the same throughout the network, and of course it integrates perfectly with Samba!

Rob


You know, after all the headache - this might be my next step. Likewise is fantastic for the Desktops, I just don't think it does what we want for Samba.

---

