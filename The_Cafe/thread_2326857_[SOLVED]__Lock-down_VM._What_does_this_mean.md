---
title: "[SOLVED]  Lock-down VM. What does this mean?"
date: 2016-06-05
forum: The Cafe
---

### Post by mikodo on 2016-06-05
Hi,

I'm not wanting a detailed discussion. I am only asking what it means to secure a host running a vm. To jail the vm if you will so, that it is isolated and it is more difficult for it to pass things malicious to the host. In my case, using KVM on my desktop machine to run vm's.

What might I use this for? Skype, safer browsing, to banking sites possibly, data streaming from paid for providers like, NHL.com. I dunno what all I would use it for in the future when, I retire. I just like the idea of isolating OS's in such an environment for the safety of it. 

So, what does this mean? No connectivity to WHAT on the host?

Thanks, for any comments.

---

### Post by DuckHook on 2016-06-05
Hi mikodo.

Yours is pretty much a security question and you will probably get great support in that forum. If you want your thread moved there, just report your own thread and one of the staff will likely look after it.

As to your question, it's not one that permits a simple answer, because real security is comprised of a number of layers, each of which hardens your system, but does not make it impenetrable. In theory, running a VM creates a sandbox that is secure in and of itself, but in order for the VM to be actually useful, most users will create openings in the sandbox to communicate with the rest of the system and this obviously will weaken security. Examples: sharing the host's "Public" folder to allow for easier file transfers, allowing the VM to connect to the internal network (and esp file servers), allowing access to host printers and usb ports, "bridged" NICs instead of NAT because doubled-NAT topographies (on most SOHO networks, your router has already created one NAT layer) create problems on some websites and file transfers, etc. You can create a highly secure environment by, for example, disabling the NIC altogether, but at the expense of your VM's utility value.

Most people don't create apparmor profiles for their VMs. Apparmor is a very effective security measure, but apparmor profiles are a steep learning curve to fine tune and maintain. You can also obviously disallow access to all network servers and don't permit the Public folder to be shared.

In the final analysis, VMs are just another tool or layer in a defence-in-depth strategy for security. They are not a magic bullet (any more than apparmor or any one tool by itself is). It's still an excellent idea to segregate some of your browsing into different VMs but this is not a substitute for good security habits. I'm sure I don't have to tell you this; it's for the benefit of others who may read this thread.

---

### Post by mikodo on 2016-06-06
> **DuckHook said:**
>  - What you said -  

Thank you!

I feared the question warranted a very technical response. I didn't want to post in "Security" as, I didn't want people to expect to give elaborate responses in all the nuances of "Locking Down" a vm. I was hoping for possibly a list of one or two word things that would constitute what is needed. I can't expect myself to ever do what you pros are doing, I was only curious what it meant to do that.

Then, you came in and gave the full-blown explanation anyway. :)

If, I could mark this as solved I would. I will put it in the title.

Then, re-read what you posted.

Have a good day!

Addendum: I re-read DuckHook's response. Truthfully, I'll never use Skype, never have but, I have had as many as 5 different Firefox profiles each, for only going to its' respective site I wanted to go to. Examples are Banking, Professional Associations, E-Purchase site that I would delete after with. So, this could be a form of that kind of internet use that might be another layer of security for me. That I could do. :)

---

### Post by lisati on 2016-06-06
> **mikodo said:**
> 
If, I could mark this as solved I would.

Unfortunately, that option isn't available in the Cafe using the "normal" method of clicking on "Thread Tools".... :(

---

### Post by mikodo on 2016-06-14
> **DuckHook said:**
>  - Snippets - 

I've never seen the word inveterate before. :)
 
[http://ubuntuforums.org/showthread.php?t=2271655](http://ubuntuforums.org/showthread.php?t=2271655)

> Not least, I am an inveterate tinkerer and just incurably curious about  LXC. If it's capable of delivering on all of the items it promises, then  it will replace my VMs for most use-cases.

In order to effectively contribute to this forum, it is useful to have  different 'buntu flavours running in tandem. Again, while this is  possible with VMs, it incurs the same resource hit as #1 above.

I have never liked the idea of running browsers on my main OS. The  browser is the single biggest security hole in all systems and even with  an apparmor profile installed, it doesn't feel like sufficient security  in depth. Yet again, the VM solution is too resource-intensive for some  machines.

Here I was looking all over trying to see how to run LXC on my desktop, if that is possible, as a replacement for KVM. Then, this thread showed up in a search.

 "The Dude abides". :smile:

> It is very apparent to me that LXC is, if not bleeding-edge, then  awfully close to being so. There are no GUI config tools (to my limited  knowledge), no how-tos beyond the very basics, and you are pretty much  on your own trying to dive any deeper than the superficial level.  Compared to the ease of installing a VM, getting LXC to run is a little  like assembling a transmission. Newbies could be quickly overwhelmed, so  approach with a realistic set of expectations

---

