---
title: "Reseting Windows NT password with Linux Iso"
date: 2008-06-16
forum: Security
---

### Post by tuproxy on 2008-06-16
I know this isn't Ubuntu, but it is Linux.  If you know somewhere I can read more about this, please point me to the correct place.  

I own a computer consulting/repair company that often deals with business PC's that have lost their admin passwords.  I have a CD that will boot to linux and reset the administrator password. I've also seen a bootable disc that can change users passwords as well.  

I know the passwords are in the WINDOWS/system32/config file, and I think are hashed.  I looked for the file in Vista, but only found a config.nt file which didn't seem to have any hashes. 

What I want to do is find out what the usernames and passwords are.  This should probably be found as hashes and decryptable with rainbow tables.  I'm hoping by learning how this is done, I can take measures to prevent this such as changing the location of the config file and moving the pointer in the registry.  I just don't want the downloadable CD's to be ableo to hack right into my PC w/o so much as a little bit of trouble.  

LMK if you can point me to a good tutorial on this or if you know how to get around this.  Thanks.

---

### Post by p_quarles on 2008-06-17
Changing the location of the password hash file isn't going to prevent your machine from being compromised by an attacker with physical access. If the registry knows where something is, the attacker too can find it.

In any case, this is ultimately a Windows question, so it would probably be more fruitful to ask in a Windows forum.

---

### Post by cdenley on 2008-06-17
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)
The version in the ubuntu repository is not the latest, and I couldn't get the free vista rainbow tables to work with it. If you are going to use it in ubuntu, you might want to compile it yourself.

You can crack most passwords in a minute. I believe the file passwords are stored in is...
WINDOWS/system32/config/sam
but you need this file to crack syskey encryption
WINDOWS/system32/config/system

---

### Post by gmendoza on 2008-06-17
> **tuproxy said:**
> 
What I want to do is find out what the usernames and passwords are.  This should probably be found as hashes and decryptable with rainbow tables.  I'm hoping by learning how this is done, I can take measures to prevent this such as changing the location of the config file and moving the pointer in the registry.  I just don't want the downloadable CD's to be ableo to hack right into my PC w/o so much as a little bit of trouble.  


For general info on pw recovery for Windows passwords... this link should give you much information and links to available tools.
[http://www.openwall.com/passwords/microsoft-windows-nt-2000-xp-2003-vista](http://www.openwall.com/passwords/microsoft-windows-nt-2000-xp-2003-vista)

The user database concepts are virtually the same for for both *nix and Windows platforms: store the username in a standard place and hash the password.  

If you want to enumerate the Windows accounts, use the appropriate pwdump variants, which also dumps the pw hash.  If you want to "recover" the original password... you run dictionary or brute force attacks against the hash (see John the Ripper).  If you want to simply reset the password... you replace the password with a new hash of your own.

In any case, as previously mentioned, while it's beneficial to learn from the above, you cannot stop this type of attack without preventing physical access to the system.  They already have access to your disk... so who cares about the password anyway.  :-)

This is where full volume encryption comes in, which helps things a great deal, but is not the "end all" of counter measures.

---

### Post by cdenley on 2008-06-17
> **gmendoza said:**
> For general info on pw recovery for Windows passwords... this link should give you much information and links to available tools.
[http://www.openwall.com/passwords/microsoft-windows-nt-2000-xp-2003-vista](http://www.openwall.com/passwords/microsoft-windows-nt-2000-xp-2003-vista)

The user database concepts are virtually the same for for both *nix and Windows platforms: store the username in a standard place and hash the password.  

If you want to enumerate the Windows accounts, use the appropriate pwdump variants, which also dumps the pw hash.  If you want to "recover" the original password... you run dictionary or brute force attacks against the hash (see John the Ripper).  If you want to simply reset the password... you replace the password with a new hash of your own.

In any case, as previously mentioned, while it's beneficial to learn from the above, you cannot stop this type of attack without preventing physical access to the system.  They already have access to your disk... so who cares about the password anyway.  :-)

This is where full volume encryption comes in, which helps things a great deal, but is not the "end all" of counter measures.

Rainbow tables is much faster than brute-force. I remember it taking hours to brute-force an NTLM hash. With rainbow tables, it takes seconds. Of course, the hardware is much faster now than the last time I brute-forced an NTLM hash. I'm not sure how the two methods would compare with identical hardware.

---

### Post by gaten on 2008-06-17
If you use passwords longer than 14 characters windows doesn't use LM hashes and forces NTLM hashes (more secure). I've also found that using spaces in passwords slows the standard ophcrack CD down.

But as mentioned by the other posters, unless you've got full disk encryption, if they have physical access to the machine they have the potential to own the machine.

---

