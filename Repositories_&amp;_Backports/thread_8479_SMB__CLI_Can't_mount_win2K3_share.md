---
title: "SMB / CLI: Can't mount win2K3 share"
date: 2004-12-17
forum: Repositories &amp; Backports
---

### Post by BertG on 2004-12-17
Hey, 

I'm new to the Ubuntu scene and I must say: i like it.
Install went a lot easyer than Gentoo! :)

Now I'm having a problem, and I think i have narrowd it down allready

so here it is.
I'd like to mount a shared folder on my win 2k3 server, so i can play it's music
I can reach the map, no problem there, but my server won't allow the mounting
hence the next error:

cli_negprot: SMB signing is mandatory and we have disabled it.
6252: protocol negotiation failed
SMB connection failed

now i got so far figuring out that i have to do something with the kernel and adding CLI to it or something...

Can annyone help me?

thx!

---

### Post by nianhbg on 2005-05-20
Hi i got a simulare problem with my windows 2003 server

I can connect to my server with smb commands in natulus
like smb://server/share i can even add a username like
smb://username@server/share and then enter a password
on password protected shares.

In xterm when i try to map a share like this

<code>
sudo mount //192.168.0.2/share /media/share
</code>

then i got a time out message on port 445 or 113


Best Regaards

Nicklas

---

### Post by Blues- on 2005-06-22
Yeap .. that is an annoying problem .. 
but here is the answer.

In a nutshell, the cause of the problem is the default security policy on Windows 2003 Server being set to always encrypt network connections under all circumstances. Whilst this is fine for most clients (especially Windows clients, understandably), the version of SMB that Panther uses doesn’t support encrypted connections. Apparently this support exists in Samba 3, but not on the version Hoary uses. The solution is to change the security policy to use encryption when it’s available and not otherwise. Here’s how.

From Administrative Tools, open Domain Controller Security Settings.
Go to Local Policies then Security Options.

Scroll down to find the entry Microsoft network server: Digitally sign communications (always). Set this to Disabled.

The only thing left to do is to reload the security policy, as changes don’t otherwise take effect for some time. Open up a command window and type:

gpupdate

This will buzz and whirr for a few moments before confirming that the policy has been reloaded. With a bit of luck you should now be able to mount a network share from the Windows 2003 Server on your Box.

---

### Post by durandal on 2005-06-27
I just installed the latest Ubuntu release yesterday and I am trying to get it integrated with the network at my office.  I am running into the same issue when I try the  "Connect to Server" option.  It connects to the server but it just keeps kicking back the password screen.  I found a post in the FAQ that said to enter the servername/share in the server name field and that didn't work as well.   

Blues - Your post looked promising but I don't see the option in the Administration control panel that you are referring too?

"from Administrative Tools, open Domain Controller Security Settings.
Go to Local Policies then Security Options."  

Has this control panel changed to something else or is it not installed by default????

---

### Post by GregW on 2005-07-21
[QUOTE=durandal]
Has this control panel changed to something else or is it not installed by default????[/QUOTE]

Hi durandal,

I doubt it, you will need to use the cifs module if you want to mount w2k3 shares, CIFS supports smb signing so you dont need to drop the security on your server.

try mount -t cifs //yoursever/yourshare /mnt/somepath -o username=validserveraccount

and then your password. 

You may need to specify the fqdn for yourserver or just add the netbios name and ip address to your host file. 

Hopefully bobs your uncle and your in business  \\:D/ 

(You will also need to update the samba debs from the backports, I've got this line in my apt sources file /etc/apt/sources.list

```
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe
``` 
GregW

---

### Post by gruvsf on 2005-12-01
GregW-
You rock! That totally did it in FC4 and I didn't have to drop the security on Win2k3....I just joined this forum and will be checking it more now for resources.

Hans

---

### Post by Benny_Blanc0 on 2006-05-19
Another two thumbs up Greg.  Cheers mate.
:D

---

### Post by cewan on 2007-05-08
You da man, GregW! Thanks alot :-)

---

### Post by Rimfrost on 2008-01-14
Greeting and many thanks to you, Greg, for saving the day. Cheers!

---

