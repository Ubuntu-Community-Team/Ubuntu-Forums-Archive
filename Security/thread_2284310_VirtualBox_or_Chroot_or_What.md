---
title: "VirtualBox or Chroot or What?"
date: 2015-06-28
forum: Security
---

### Post by Alebin on 2015-06-28
If I'm looking to run a questionable program, maybe it could one day be exploited terribly (like Firefox and Flash or something), and want it to be in its own little 'box' that can't affect my main system if something would happen, what is the best route? Do I use chroots, virtualbox, or something else? Maybe things can be layered? Also any hardening tips on the usage of said method would be appreciated.

Edit:
I forgot to include that I need to have some way of accessing the files inside this 'box' and pulling them selectively out and onto my main system if the need arises. Also, if it uses internet access, it will need to use the host's connection.

---

### Post by ajgreeny on 2015-06-28
I would love to know what you mean by a "questionable program", but I think VBox will probably be easiest for you, and it can do all that you ask about;  the guest OS is effectively "sandboxed" in its own .vdi file, and by taking regular snapshots you can always have a recent fallback, or backup, should the current guest OS be compromised in any way.

You can also share folders between the host and guest by installing the VBox guest-additions, enabling you to get to all the files from the guest onto the host if you need to.

Internet connection should not be a problem provided the host is connected.

VBox is available in the repos, and that may be the easiest for you, but personally, I have always installed the more recent version in my Xubuntu 14.04 direct from Oracle, along with the guest-additions.
[Downloads &#8211; Oracle VM VirtualBox]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by Alebin on 2015-06-28
I've heard about malware possibly being able to 'break out' of VirtualBox before, and chroot for that matter. That is what concerns me. The guest OS would be Ubuntu or Debian in my case also.

Edit:
I suppose one could VirtualBox a guest OS, then chroot the application. I wonder if that's the best solution though and that's why I'm asking on here.

---

### Post by ajgreeny on 2015-06-28
> **Alebin said:**
> I've heard about malware possibly being able to 'break out' of VirtualBox before, and chroot for that matter. That is what concerns me. The guest OS would be Ubuntu or Debian in my case also.
That is something I have not heard about, and there is a recent thread asking about that very situation at [http://ubuntuforums.org/showthread.php?t=2283154&p=13306727#post13306727](http://ubuntuforums.org/showthread.php?t=2283154&p=13306727#post13306727)

---

### Post by Alebin on 2015-06-28
I just switched from Win8.1 and I'm trying to lock things down as much as I can in a super paranoid way. I'm installing aide as I post this. I guess I will give the VirtualBox a go and maybe chroot inside it as well. I just don't particularly like the idea of installing something so 'grasping' as VirtualBox, but I suppose the source gets reviewed decently by Ubuntu and other folks and it's better to trust one pathway like this than to run other 'questionable programs' on the bare install of Ubuntu.

Thanks for the help. I will check back for other possible suggestions, but in the mean time I will give this a go.

---

### Post by matt_symes on 2015-06-29
Hi

There have been escapes from both chroots and virtual machines and I expect new vulnerabilities will be discovered in the future.

Nothing is totally secure but just remember the mantra "defence in depth" and, if you're really worried about this questionable program, then running said program in either a chroot or virtual machine can be part of that strategy.

Kind regards

---

