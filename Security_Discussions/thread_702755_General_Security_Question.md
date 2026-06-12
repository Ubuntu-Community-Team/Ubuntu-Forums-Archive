---
title: "General Security Question"
date: 2008-02-20
forum: Security Discussions
---

### Post by sharpnotflat on 2008-02-20
I heard Linux is more prone to viruses than Windows and Mac. Is this true?

If so, what antivirus software can I install for my Ubuntu Gutsy?

---

### Post by tubezninja on 2008-02-20
Just curious, who told you this? 

A handful of viruses do exist for linux, but the list pales in comparison to the 200,000+ viruses that exist for Windows.  And there's one other immense difference: nearly all of the viruses that affect linux require some level of complicity by the user, whether it be running a program from an untrusted source, or deliberately running code to see what harm it can do, or even just failing to patch and update the kernel against security threats, despite the ease in doing so.

On the other hand, with a Windows machine, all you have to do is boot Windows without a firewall or virus protection software, hook it up to the network, and let it sit.

Here's a comprehensive list of virus statistics:

[http://en.wikipedia.org/wiki/Virus_statistics](http://en.wikipedia.org/wiki/Virus_statistics)

Note: there's only about 36 or so Linux viruses, and if you're running the latest Ubuntu patches, you're pretty well protected against them.

If, however, you want to scan for viruses, the most comonly cited on-demand virus scanner for linux is clamAV.  All you have to do is drop into a terminal session on your ubuntu box and type:

```
sudo apt-get install clamav
```

And it'll install. :)  Most people (including myself) run it because even though the threat on linux is relatively low, it's considered good practice to make sure your linux box or server isn't harboring any files infected with Windows viruses that a Windows user may later access and infect themselves with.  Just because a Windows virus can't hurt us, doesn't mean we should be spreading them, even accidentally.

---

### Post by HermanAB on 2008-02-21
Here is an explanation:
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

