---
title: "Please don't flame me too badly for this question.."
date: 2010-01-12
forum: Server Platforms
---

### Post by akakingess on 2010-01-12
I am currently running Ubuntu Karmic Desktop on 2 of my home computers along with 2 other Windows macines and am looking to turn 1 of the Karmic machines into a semi-server. I want to use it as central storage and a possible central calendar  amongst other little things of that nature. However, I am having the hardest time with Samba working the way that I want it and was wondering if there would be a problem with turning the "server" machine into a true "Domain Controller" to make things simpler (I know that sounds backwards), but I would still like to use the so-called "domain controller" as a normal desktop to do email, internet, and some web design. It is a dual-processor 64-bit machine with 4 GB of RAM. So, I guess my main question would be could anyone see any drawbacks to turning the "server" into a true Domain Controller and still being able to use it as a normal desktop computer as long as I install a desktop GUI (preferably Gnome)? If this would be acceptable (remember this is just for (4) computers including the "server" and for home use only (so not too demanding) and if so, what would be the best way to go about it? I have backup drives to back everything up, etc., it's just a matter of whether I should keep trying to deal with Samba or go all-out and turn it into a DC?  Thanks in advance for taking it easy on me and any and all advice )including constructive criticism is more than welcome.  Thanks again.

EDIT: I love to read and any links to sites or E-Books are definitely welcome as well, thanks again.

---

### Post by noway2 on 2010-01-13
This has become a frequently asked question and I am not surprised that you are confused over it given the often times conflicting responses.  Most of the threads on this subject conclude that a "desktop" with a GUI is absolutely capable of performing the functions traditionally assigned to a "server".  Consequently, the answer to your question is almost certainly, yes your system will be capable of doing what you want.  A traditional "server" is predominately accessed remotely so that it doesn't have much need to a GUI.  Since it does not have need for one, the "server" build can take advantage of this and be optimized for better performance as well as eliminate some possible security holes. For your home environment, these differences are minor at best and shouldn't have an appreciable impact.

I am not quite certain what you mean by "domain controller" in terms of a home network.  Per Wikipedia, a domain controller predominately handles authentication on a Windows Network.  I would be surprised if Samba wasn't capable of meeting your needs but if you need authentication, there are other methods such as LDAP and Kerberos, which are probably mass overkill for your environment.  Before going that route, consider reading a book called Samba by Example (or something similar) that may answer your questions.

Again to reiterate, your "desktop" should be more than sufficient to host a file server, email server, DHCP, DNS, SQL server, SSh server, etc.  For a home or small office environment it is simply not necessary to use dedicated "server" hardware or a "server" OS.

---

### Post by akakingess on 2010-01-13
Thank you so much for taking it easy on me, as you are 100%, the options and differing opinions were throwing me off a bit, it just seems that I have had so much trouble with Samba that I thought a more traditional server route may be the way to go, but now I think I will take your sage advice and read Samba by Example (like I said, I love to read) so hopefully all of my answers or at least the holes that I have lacking within Samba will be answered. Thanks again for taking the time to help out someone that is semi-fluent on the desktop version, just seemed to be getting nowhere fast in regards to sharing my Central Storage Drives on Ubuntu with the rest of the Windows world.

---

### Post by pirateghost on 2010-01-13
i tried making a linux only 'active directory' for my windows boxes at home...it failed.  i got authentication working with little effort, but i needed a more robust AD environment so i wound up falling back to a windows domain controller...

having said that, there is no true reason to have an active directory in your home environment unless you just simply want to learn more about it.  it is not required to create a centralized storage server, and only complicates things if it were to break.

if what you are in the market for is a simple fileserver/NAS situation, then keep it simple and set up a SAMBA share.  if you dont need authentication against that share within your network then set it to be a share level rather than a user level share.

AD is a big deal and when it breaks, be prepared to do some major troubleshooting....

---

### Post by neoanderthal on 2010-01-14
For a home network, unless you're integrating into an existing AD topology I would just stick with the NT4-style PDC setup in Samba. You shouldn't have too much trouble setting up a pretty simple Samba server to do this: all of your user accounts would be managed on the Samba server, so you shouldn't encounter the finicky file permissions joy when you're trying to map/inherit AD permissions onto the *nix file permissions.

---

### Post by akakingess on 2010-01-14
> **neoanderthal said:**
> For a home network, unless you're integrating into an existing AD topology I would just stick with the NT4-style PDC setup in Samba. You shouldn't have too much trouble setting up a pretty simple Samba server to do this: all of your user accounts would be managed on the Samba server, so you shouldn't encounter the finicky file permissions joy when you're trying to map/inherit AD permissions onto the *nix file permissions.

By PDC, I am assuming you mean Primary Domain Controller, which is actually the way that I wanted to set it up, mainly because I am having the hardest time with Samba, it is being finicky (for lack of a better word) on me. So, what you are saying is that setting this machine up as a Primary Domain Controller and also being able to use it as a normal desktop machine shouldn't be too much of an issue? If so, than that is definitely what I intend to do. However, could someone point me towards a guide to getting Gnome set up on the server (once I convert this one over to the Server install) without too much hassle? Or should I be able to just keep it as a desktop installation and choose PDC as the option from within Samba (although that would not be my personal preference).

---

### Post by neoanderthal on 2010-01-14
Yep, you got it.

You should be able to 'apt-get install ubuntu-desktop' to set up a desktop environment on your server.

You can simply add the samba package to your existing installation if you want. The initial configuration of the workstation and server versions differs somewhat, but there's no practical difference in packages.

---

