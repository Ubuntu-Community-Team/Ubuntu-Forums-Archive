---
title: "Having trouble setting up ProtonVPN (NEW USER)"
date: 2021-03-22
forum: Security
---

### Post by red783 on 2021-03-22
Hey guys I had to reinstall my release of Ubuntu, and I'm having trouble getting ProtonVPN set up. I follow Protons online instructions but i get to a certain point in the command line and doesn't want to continue. I'll include what I see in my terminal.
__________________

$  sudo add-apt-repository 'deb [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) unstable main'
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Ign:4 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Hit:5 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:7 [http://ppa.launchpad.net/flexiondotorg/minecraft/ubuntu](http://ppa.launchpad.net/flexiondotorg/minecraft/ubuntu) focal InRelease  
Get:8 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [3,316 B]                 
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease              
Hit:11 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease          
Hit:12 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) unstable InRelease
Err:8 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D1742AD60D811D58
Reading package lists... Done
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D1742AD60D811D58
E: The repository 'http://repository.spotify.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Skipping acquire of configured file 'main/source/Sources' as repository 'https://repo.protonvpn.com/debian unstable InRelease' does not seem to provide it (sources.list entry misspelt?)
______________

If anyone can help that would be awesome.

Thanks in advance,
red7800 ( I know it says 783. I gotta "post 10 times???" Anyway...)

---

### Post by TheFu on 2021-03-22
The 1st problem is with spotify.  Remove that from your repo list however you added it.  The output says you should look at the apt-secure manpage, section 8. Have you done that? If it was me, I'd just comment out the [http://repository.spotify.com](http://repository.spotify.com)  line in whatever sources.d file(s) it is.  Then run **sudo apt update && sudo apt full-upgrade** .

When troubleshooting problems. Fix those that happen first, since they may also fix some later errors.

[https://protonvpn.com/support/linux-vpn-setup/](https://protonvpn.com/support/linux-vpn-setup/) appears to have out of date instructions, since resolvconf has been deprecated for systemd-resolved instead.  Maybe contact support about that. Perhaps you are following different instructions? Please don't make us search and guess for things obvious to you.

These instructions [https://www.fosslinux.com/45387/install-protonvpn-linux.htm](https://www.fosslinux.com/45387/install-protonvpn-linux.htm)  from 2 months ago don't say that either. 
I'm confused. Not that unusual. ;)

Trying to use a debian unstable repo with Ubuntu is asking for APT problems.  I did see a beta release from proton, however.  Do you really want to have a paid VPN, but use a beta release of their packages and installer? [https://protonvpn.com/support/official-linux-client/](https://protonvpn.com/support/official-linux-client/) are the instructions. It claims that 20.04 will work. 
Which Ubuntu release do you have?  
Did you follow the Ubuntu-specific steps?
Did you read the "Notes"?

I tried to visit [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) and it doesn't exist.  In short, don't use those instructions.

---

