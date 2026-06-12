---
title: "SELinux sandbox on Ubuntu"
date: 2011-04-08
forum: Security
---

### Post by adagio on 2011-04-08
Have just read this article on the SELinux sandbox:

[Run Applications in Secure Sandboxes with SELinux]("http://www.linux.com/learn/tutorials/382226:run-applications-in-secure-sandboxes-with-selinux")

As far as I can see though from [pkgs.org]("http://pkgs.org") at least Fedora is the only dist to include the sandbox util.

Would be really gr8 to see this in Ubuntu :)

Or does AppAmor have similar functionality - I will take a look at the pinned thread.

---

### Post by bodhi.zazen on 2011-04-08
Ubuntu uses Apparmor. I confine the guest account using "jailbash"

For general advice, see:

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

I should probably cover that in more detail on my blog or web pages ;)

---

### Post by HermanAB on 2011-04-10
Howdy,

You can install SELinux on Ubuntu, but then NOTHING will work, since it is not configured and configuring it will be a lifetime mission.

So, if you really want to play with SELinux, install Fedora, otherwise, use AppArmor.

There are many Mandatory Access Control systems.  the best ones are:
SELinux, AppArmor and Tomoyo Linux.

---

### Post by js31 on 2011-06-01
May not be the right place to ask, but: There are many comparisons online; for a newbie it can be difficult to choose. Is it right that only SELinux's sandbox engages an X instance and window manager of its own? The other features seem comparable to me, except performance.

---

### Post by Lars Noodén on 2011-06-01
> **bodhi.zazen said:**
> Ubuntu uses Apparmor. 

Does AppArmor have anything to do with systrace?

---

### Post by bodhi.zazen on 2011-06-01
> **Lars Noodén said:**
> Does AppArmor have anything to do with systrace?

What are you wanting to know ?

Apparmor can restrict the root account and I do not see any reason you can not limit access to systrace with apparmor.

---

### Post by Lars Noodén on 2011-06-01
> **bodhi.zazen said:**
> What are you wanting to know ?

Apparmor can restrict the root account and I do not see any reason you can not limit access to systrace with apparmor.

That answers part of the question indirectly.  AppArmor must be something separate, even though it sounds similar. [systrace](http://www.citi.umich.edu/u/provos/systrace/) can restrict which files (even sockets and devices) a program can access.

---

### Post by bodhi.zazen on 2011-06-01
From your other posts on the subject, I think you should read up and test apparmor and/or selinux

---

### Post by Lars Noodén on 2011-06-01
What are the three best web pages for getting started with AppArmor?

---

### Post by Rubi1200 on 2011-06-01
Hi Lars,
not sure what bodhi would recommend, but you should definitely take a look here:
[http://en.opensuse.org/SDB:AppArmor_geeks](http://en.opensuse.org/SDB:AppArmor_geeks)

and here:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by bodhi.zazen on 2011-06-01
> **Lars Noodén said:**
> What are the three best web pages for getting started with AppArmor?

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

---

### Post by js31 on 2011-06-03
@bodhi.zazen
Thanks for the great tutorials + Firefox-profile! Managed to set it up using them. =)

--

Just wondering, for non-techies, how reliable do you guys estimate the protection of AppArmor versus Adobe Flash 0-days?

I set up my system real secure with VPN, firewalls etc., but my PC's too slow for WebM. When I stumble over sites with embedded political YouTube videos, which NoScript doesn't block if you enabled Google's service, kinda makes me feel paranoid... :'

---

### Post by bodhi.zazen on 2011-06-03
There is no perfect solution or absolute security, but apparmor is as good as it gets (on Ubuntu) in terms of hardening.

---

### Post by Lars Noodén on 2011-06-03
> **js31 said:**
> Just wondering, for non-techies, how reliable do you guys estimate the protection of AppArmor versus Adobe Flash 0-days?


You can look in the profile, it should be in /etc/apparmor.d/usr.bin.firefox, to see what is allowed and not allowed.  It may be daunting in volume, but is not that complex.

---

### Post by js31 on 2011-06-03
@Lars Noodén
Thanks, and I had tried, should have said that. I'm a bit insecure about if I need to create a seperate file usr.lib.firefox.plugin-container (e.g. [this one]("http://www.banchixi.com/linux/apparmor/index.html")) or if AppArmor expects the rules in usr.bin.firefox - can't find something on that, however no errors so far when merged.

---

### Post by jebus_beler on 2011-11-14
The link in the original post explains how SELinux can be used to restrict network access of a given application.  I've been trying to find a way to do this with AppArmor but have not found a good reference yet.  I basically want to block an application from accessing the network at any layer (i.e. not just tcp but even raw or icmp or whatever). Can someone point me to some references or, better yet, a functional profile I can use as a baseline?

Thanks

---

### Post by bodhi.zazen on 2011-11-14
> **jebus_beler said:**
> The link in the original post explains how SELinux can be used to restrict network access of a given application.  I've been trying to find a way to do this with AppArmor but have not found a good reference yet.  I basically want to block an application from accessing the network at any layer (i.e. not just tcp but even raw or icmp or whatever). Can someone point me to some references or, better yet, a functional profile I can use as a baseline?

Thanks

Most any apparmor guide can show you how to do this. Make a profile for your application and deny network access.

---

### Post by jebus_beler on 2011-11-14
Thanks bodhizazen, but I'm finding a lot of documentation on prohibiting access to the filesystem but much less to the network.  

If I understand the apparmor.d manpage correctly not specifying a "network" directive in a profile will block the application from accessing the network.  Does this also block raw access to the network device or do I somehow have to disable that capability?  

My apologies if these questions are answered somewhere but the documentation doesn't seem very clear -- hence the desire for an example.  Unfortunately I can't test this in the context I'm interested in until tomorrow...

---

### Post by Lars Noodén on 2011-11-14
> **bodhi.zazen said:**
> Most any apparmor guide can show you how to do this. Make a profile for your application and deny network access.

I recall reading that network access controls were being added.  Has AppArmor gained the ability to restrict applications to specific ports or protocols yet?  The guides and howtos don't cover this yet.

---

### Post by Dangertux on 2011-11-14
> **Lars Noodén said:**
> I recall reading that network access controls were being added.  Has AppArmor gained the ability to restrict applications to specific ports or protocols yet?  The guides and howtos don't cover this yet.

Yes Apparmor has all types of nifty methods for limiting via network types, even expressions for control based on source addresses, ports all that good jazz.

You can find out more here : [http://wiki.apparmor.net/index.php/AppArmor_Core_Policy_Reference](http://wiki.apparmor.net/index.php/AppArmor_Core_Policy_Reference)

---

### Post by jebus_beler on 2011-11-14
> **Dangertux said:**
> You can find out more here : [http://wiki.apparmor.net/index.php/AppArmor_Core_Policy_Reference](http://wiki.apparmor.net/index.php/AppArmor_Core_Policy_Reference)

This looks like a useful ref, thanks!  I'll check it out.

I found some of this info already via manpages and using the aa-profgen app but I'm finding that the profile generated by the latter is somehow blocking the application from doing other things it needs to do (accessing some temp file or some shared memory, or something else it needs).  Unfortunately I can't figure out exactly what is being blocked because the log only shows DENIES of "inet dgram" stuff and I know that can't be the problem because the application works when I'm offline.  Could inet dgram refer to some internal sockets used to communicate between processes?  

Is there a way to only disable external network access while not enforcing any other constraints i.e. on local sockets and on the filesystem?  I mean what's the default behaviour of apparmor if you don't have a rule for something?  I want to essential let the application do anything by default and then only block the things I want...is there a way to do this?

---

### Post by Dangertux on 2011-11-14
> **jebus_beler said:**
> This looks like a useful ref, thanks!  I'll check it out.

I found some of this info already via manpages and using the aa-profgen app but I'm finding that the profile generated by the latter is somehow blocking the application from doing other things it needs to do (accessing some temp file or some shared memory, or something else it needs).  Unfortunately I can't figure out exactly what is being blocked because the log only shows DENIES of "inet dgram" stuff and I know that can't be the problem because the application works when I'm offline.  Could inet dgram refer to some internal sockets used to communicate between processes?  

Is there a way to only disable external network access while not enforcing any other constraints i.e. on local sockets and on the filesystem?  I mean what's the default behaviour of apparmor if you don't have a rule for something?  I want to essential let the application do anything by default and then only block the things I want...is there a way to do this?

If you look in that guide for address based expressions, it should be able to do what you need. In terms of restricting socket creation.

---

