---
title: "Noob needs some help"
date: 2009-12-21
forum: Ubuntu Studio
---

### Post by jm951 on 2009-12-21
Ok, I've installed Ubuntu 9.10, so far I like it. The main purpose I'm using it is for video production. I use Sony Vegas Pro in Vista, but would like to move away from the windows OS because I've never liked the idea of lining Mr. Gates pockets further. I've installed Cinelerra and Kdenlive. Both are having issues, but Kdenlive has been the real problem child at the moment. It crashed repeatedly on a test project i was doing to learn the software. I tried to follow the instructions for debugging by creating a trace. There are some problems with both software packages, but I'll deal with that later. What I'd like to do is undo trying to generate a trace file. Here is the page i was following-

[https://wiki.kubuntu.org/DebuggingProgramCrash](https://wiki.kubuntu.org/DebuggingProgramCrash)

Section I was following is under the Hardy 8.04 and Newer heading. I followed the section related to using the Synaptic Package Manager and then entering the "sudo" commands from the terminal.

The result- Kdnlive doesn't run much better, I get an error message when I attempt to start the Synaptic Program Manager-

E: Type 'exit' is not known on line 1 in source list /ept/apt/sources.list.d/ddebs.list
E: The list of sources could not be read
Go to the repository dialog to correct the problem
E:_cache->open() failed, please report.

Version of Ubuntu I'm running- 9.10 fully updated as of 12/19/09
Machine- Gateway
Processor-  AMD Athlon 64 x2 Dual Core 5000+

So how do I go about undoing the attempt at tracing the bug and getting the Synaptic Package Manager back up and running? I'll then return to getting Cinelerra and Kdenlive functioning properly.

Thanks in advance..........

---

### Post by oldos2er on 2009-12-21
Can you run this command and post the output here?

```
cat /etc/apt/sources.list.d/ddebs.list
```

---

### Post by jm951 on 2009-12-21
> **oldos2er said:**
> Can you run this command and post the output here?

```
cat /etc/apt/sources.list.d/ddebs.list
```

Ran the command- output-

exit

With the command line ready for further input

---

### Post by oldos2er on 2009-12-21
Did you create that file yourself? Kinda wondering how it got there, and why it's broken.

You can fix it by running ```
sudo rm /etc/apt/sources.list.d/ddebs.list && sudo apt-get update
```

---

### Post by jm951 on 2009-12-22
Thanks a bunch, that solved it.

I created the file by following the instructions listed in-

[https://wiki.kubuntu.org/DebuggingProgramCrash](https://wiki.kubuntu.org/DebuggingProgramCrash)

There wasn't anything listed on how to undo it. I haven't done any programming to speak of since MSDOS 6.22. I did have to do some UNIX when doing CAD back in a previous lifetime. Always liked UNIX, now have a really good reason to dive right in.

Now back to getting Kdenlive and Cinelerra running properly.

---

