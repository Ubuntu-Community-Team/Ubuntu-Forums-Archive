---
title: "neighbor hacks  my system from a wireless router"
date: 2011-03-13
forum: Security
---

### Post by Care on 2011-03-13
I have a major problem since having some electrical work done.  I believe a router is hidden in my house, which a neighbor uses to access my Ubuntu system maliciously.  I am currently using Ubuntu 8.1, and have repatedly tried to install upgrades & updates only to find crucial settings changed or synaptic packages removed.  I bought a Ubuntu 10.10 alternate cd to install hopng that if I avoided the internet that he could not tamper with the installation.  However it only formatted 33%, and it had errors which included a missing numlockx package.  I even bought a WFI jammer, but this didn't help.  I'm at my wits end, any help would be much appeciated!:confused:

---

### Post by bapoumba on 2011-03-13
Moved to Security Discussions.

How can you tell your Ubuntu machine is being compromised ? Which settings are being changed ?
When you install Ubuntu, you create an account with a password. Is this the account being accessed ?

When running updates and or upgrades, it is usual to see packages removed. The update manager or synaptic tell you which packages will be removed before you accept the upgrade. 

As for a hidden router, I would advise having some (other) professional come over and check your installation.

---

### Post by no2498 on 2011-03-13
? do you have a router of your own in the house 
if yes turn off the wire less

---

### Post by oldos2er on 2011-03-13
8.10 is no longer supported; it's repositories have moved to the old releases repositories: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by bapoumba on 2011-03-13
> **oldos2er said:**
> 8.10 is no longer supported; it's repositories have moved to the old releases repositories: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
Good point :)
update should give errors though if they are not using the proper repos.

---

### Post by Eiji Takanaka on 2011-03-13
First of all relax dude.

Secondly if your neighbour was that keen on accessing info from your computer, and that involved hiding a router somewhere in your house, and having the technical know-how to redirect your browser to a page with a bogus alternate copy of ubuntu 10.10 then they more than likely have allready accessed all your files. 

You see if it was someone experienced then i imagine you wouild have absolutely no idea they had been on your system at all in the first place.

Did you check the md5sum of the 10.10 .iso before you installed it?

What exactly is making you think you are being 'hacked'?

---

### Post by Eiji Takanaka on 2011-03-13
But if you wish to see all network traffic connected to your computer, i would checkinh out a program called 'wireshark'. Or similar network deep packet analyser of your preferred flavour. 

This will give you the ability to analyse and log in real-time (or off-line as well;) all traffic that flows over your local subnet. (wifi network). This includes anyone who might of somehow breached your wifi security. Unless of course you download an altered copy of wireshark and that is compromised in itself. 

In which case the best course of action may well be to 'don a disguise (perhaps a large beard and glasses). Go out and obtain a different laptop. Download independently and from an uncompromised source a fresh copy of ubuntu 10.10. check the md5sum and all the other verficiation systems. To make sure its legit. Upon confirmation of this link directly to the synaptic package manager and update all the latest patches/security vulnerabilities e.t.c. Upon verifying this secure system return back home. Get a new router. Employ wpa2 ccmp/aes enterprise standard encyrption.

Just remember to change the routers backdoor entrance to something other than admin/admin.

Then perhapos your system will be safe. 

That is of course if the ever so trusted sourc es (repositories) haven't been compromised, which to me would be the first logical place to compromise if you wanted to keep an eye on fairly free-thinking individuals.

Hope this helps!

;)

---

### Post by rubylaser on 2011-03-13
And, have you tried to hook your computer directly up to your internet modem, and completely unwire (separate it) from the rest of the network?  Unless your ISP's modem has wireless built-in, there would be absolutely no way for your neighbor to connect, even if they have setup a rouge access point.  If your ISP's modem has wifi, disable it.

Once you've done these things, install Ubuntu, setup a user account with a strong password (not one you normally use).  This whole scenario seems a little bit strange to me.  How did your neighbor setup an access point in your house without you knowing?  He would have had to break-in, and if you really believe that's the case, I'd be contacting law enforcement.

---

### Post by pbpersson on 2011-03-14
> **rubylaser said:**
>  How did your neighbor setup an access point in your house without you knowing?  He would have had to break-in, and if you really believe that's the case, I'd be contacting law enforcement.

The OP said he had some electrical work done in his house.  Reading between the lines, I assumed the electrician was the one who hid the router in the walls of the house as part of a grand scheme on the part of the neighbor.

But maybe I have it all wrong

---

