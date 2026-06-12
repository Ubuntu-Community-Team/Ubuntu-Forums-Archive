---
title: "Setting up virtual machines"
date: 2010-10-26
forum: Virtualisation
---

### Post by griztown on 2010-10-26
Hi all.  I recently read [this article]("http://www.tomshardware.com/reviews/joanna-rutkowska-rootkit,2356.html") on Tom's Hardware guide that put me on to some cool aspects of virtualization.  Namely this portion of the article for maximizing security:

> Alan: How about some practical tips? Although most of your research involves the bleeding edge of security research, the vast majority of malware currently in the wild does not operate at levels this close to the metal. How should our readers secure their own system?

Joanna: That's a very generic question and it is hard to give one answer that would fit all.

Alan: What do you do for your regular systems?

Joanna: First, as stated, I believe in the Security by Isolation approach. The problem is, however, that all current popular OSes, like Vista, Mac OS X, or even Linux, do not provide a decent isolation to its applications. This is primarily a result of all those systems using big monolithic kernels that consists of hundreds of third-party drivers that operate at the same privilege level as the rest of the kernel. As a result, it is relatively easy for a malicious application to break into the kernel and consequently to bypass any OS-provided security mechanisms.

So, I'm trying to get around this weak isolation by using virtualization. I use different virtual machines to host various types of browsers that I use for different kind of activities. So, I use a "Red" VM to do daily browsing, something totally non-sensitive like news reading, Googling, etc. I use a "Yellow" machine to do some semi-sensitive tasks, like online shopping, updating my blog on Blogger, etc. Finally, I have a "Green" machine to access my bank's account.

I totally don't care about a compromise of my "Red" machine--in fact I revert it to a known snapshot every week or so. I care much more about my "Yellow" machine. For example, I use NoScript in a browser I have there to only allow scripting from the few sites that I really want to visit (few online shops, blogger, etc). Sure, somebody might do a man-in-the-middle (MITM) attack against a plaintext HTTP connection that is whitelisted by NoScript and inject some malicious drive-by exploit, but then again, Yellow machine is only semi-sensitive and there would not be a big tragedy if somebody stole the information from it. Finally, the "Green" machine should be allowed to do only HTTPS connections to only my banking site. It is quite important to make sure only HTTPS is used for this machine to mitigate potential MITM attacks, that might occur, for example on any hotel Wi-Fi.

I've been using this setup for quite a while and it seems to work pretty well for me. My partner, who is a totally non-tech person, also uses a similar setup on her Mac, and she finds it usable. So, I guess it's not as geeky as it might sound.

There are quite a few more details one should also consider when using such a setup, for example handling updates, the use of clipboard, the transfer of files between the machines and the host, where to keep one's email client, why to use a Green machine and not just the host's browser, etc. But I guess this is not the best place to go into all of the details now, or our interview would transition into a How To.

Still, I cannot say I'm totally satisfied with my setup. To run all of my virtual machines, I use a type II hypervisor (VMWare Fusion), which is a fat application running on my host. From the theoretical point of view, there is no good reason to believe that it would be harder to find a bug in the type II hypervisor than it would be to find a bug in the OS kernel itself. Both are big and fat, and have many drivers inside them. But practically, it seems that it is more difficult. The attacker must first find a way to execute code in the guest's kernel. Remember that the attack starts from being able to execute code in the browser only, then he or she must find a way to attack the VMM (hypervisor). So, to break out of the VM and finally do something reasonable in the host's kernel, which might be a totally different OS then the guest's kernel (I use Windows in my guests and Mac OS X on the host).

This sounded intriguing and I've been trying to figure out how to set something like this up.

I already use VirtualBox on my current desktop to run Windows XP, hosted by Ubuntu 10.04.  Problem is this desktop is ancient and needs replacing.  I've been looking around and it seems there are many options for setting up a system to maximize virtual machine performance.  

For example, I read about IOMMU in AMD's 890fx chipset.  Seems like a nice thing to have.  

So does anyone recommend hardware for building a desktop that could maximize VM performance?  I'm currently thinking of a Phenom II X6 1055T with an ASUS 890FX mobo.  I had been leaning towards the 890GX since it's cheaper and has a built in video card but I hate to leave IOMMU off the table.  So how valuable is IOMMU to virtualization?  I'm assuming this setup would support [AMD-V]("http://en.wikipedia.org/wiki/X86_virtualization#AMD_virtualization_.28AMD-V.29").

Let me know what you think.  Thanks!

---

### Post by HermanAB on 2010-10-27
Mainly, you just need a ton of RAM.

---

### Post by dcstar on 2010-10-27
> **griztown said:**
> Hi all.  I recently read [this article]("http://www.tomshardware.com/reviews/joanna-rutkowska-rootkit,2356.html") on Tom's Hardware guide that put me on to some cool aspects of virtualization.  Namely this portion of the article for maximizing security:
..........
Let me know what you think.  Thanks!

Blah blah blah..... firstly the generalisation in the article about "hundreds of third-party drivers" is total BS when it comes to Linux, to use a single "third-party driver" in Ubuntu you have to deliberately choose to do so.

If someone wants to run various VMs (probably Windows VMs) because they are paranoid about security then good on 'em, they can use one of them to safely buy a new foil hat to keep the death-rays the aliens keep sending at bay....

Show us some real examples of hosts being compromised by VMs and some of us might just take these "frighten the horses" articles seriously.

Use VMs for convenience being aware that anything running in a non-native environment and sharing resources will not run as well as a native install, so spec your VM host hardware at a higher level to compensate for that reality, as previously posted more RAM is the best way to do that.

---

### Post by griztown on 2010-10-27
I apologize if this came off as being an attack on Ubuntu and linux.  I certainly did not mean to do that!  I definitely believe that linux and Ubuntu is far more secure than Windows.  I guess I was just impressed with the idea of using a VM to do your online banking, etc.  Seemed like a good idea.  

So does anyone have any experience with IOMMU?  What I'm really struggling with now is if I should pay extra for that feature.  I definitely want to use virtual machines and would like to get maximimum performance.  Does IOMMU buy much or is just having tons of RAM sufficient?

---

### Post by gamebusterzade on 2010-10-27
tell u what if ur are that serous about doing a VM get a computer with a 64bit OS (so u can see and use more than 3GB of Ram), at lest 3GB ram, a CPU that suports virtualization (VT-x/AMD-V), and if u like to multi-task get a graphics card that support dual monitors

as for as i can tell IOMMU may help with speed but may and will are two different things

other than that u should be good

Also larger the hard drive the better if u run multiple VM for they do take up a dedicated amount of space on the hdd

---

### Post by ubaddn on 2010-11-07
. I am so thankful
this article was pointed out us;
for 2 years I've been using
mac.vmware`fusion to run ubuntu
-- worried about rootkits --
but since recently hearing about
Joanna Rutkowska's expertise in rootkits
I wondered how her setup differed from mine .

. I was suprised she did her online shopping
on a separate machine from her banking;
but she's right, once at macmall (a secure site)
I got my credit card "validated" by a scam;
who knows what else I got?
(I think macmall uses 3rd-party advertizing).

. as for linux having no 3rd-party drivers:
in security terms,
all open source is 3rd-party!
it's a lot of cooks in the kitchen;
complexity increases risk .
. did you know that most of
russia, china, the world,
are using bootleg microsoft?
when the world moves to linux,
the botnets will come for linux next !

. but by the time they do,
we will be saved by ...
#  intel's VT-d, TXT, TPM,
# linux (or anything) on the
okL4 verified microvisor
# and using Joanna's system of
5 vm's for each security domain,
-- or [Joanna's Qubes]("http://theinvisiblethings.blogspot.com/2010/10/qubes-alpha-3.html")

**5 vm's for each security level:**
# red: browsing random sites, no privacy;
-- expected to get infected;
. I revert it to a known snapshot every week or so.
# yellow: semi-sensitive tasks,
. uses firefox.NoScript to only allow
 scripting to a trusted few sites:
  online shopping, blogging, etc.
Sure, somebody might do a
 man-in-the-middle (MITM) attack against
a plaintext HTTP connection
that is whitelisted by NoScript
and inject some malicious drive-by exploit,
but then again,
Yellow machine is only semi-sensitive
and there would not be a big tragedy
if somebody stole the information from it.
[unless credit cards are used?
maybe that's for green vm?]
# green:  https-only, bank's account
. it is quite important to make sure
only HTTPS is used for this machine
to mitigate potential MITM attacks;
for example, on any hotel Wi-Fi.
.  don't use the host's browser as a Green machine:
[the host is a huge attack vector;
and, all the attacks are coming from online;
so, take it offline .]
# [where to keep one's email client:]("http://qubes-os.org/Architecture.html")
[with separate personal and work vm's;
both have mozilla mail;
work needs a noscript browser]

**other tips:**
#handling updates:
[getting prompt updates for each guest vm
dramatically reduces the number of attacks .]
# clipboard:
[every guest can be logging the clipboard .]
transfer of files between vm's and host:
[more networking is more risk .]

---

### Post by Rarez on 2010-11-08
> **ubaddn said:**
> . I am so thankful
this article was pointed out us;
for 2 years I've been using
mac.vmware`fusion to run ubuntu
-- worried about rootkits --
but since recently hearing about
Joanna Rutkowska's expertise in rootkits
I wondered how her setup differed from mine .

. I was suprised she did her online shopping
on a separate machine from her banking;
but she's right, once at macmall (a secure site)
I got my credit card "validated" by a scam;
who knows what else I got?
(I think macmall uses 3rd-party advertizing).

. as for linux having no 3rd-party drivers:
in security terms,
all open source is 3rd-party!
it's a lot of cooks in the kitchen;
complexity increases risk .
. did you know that most of
russia, china, the world,
are using bootleg microsoft?
when the world moves to linux,
the botnets will come for linux next !

. but by the time they do,
we will be saved by ...
#  intel's VT-d, TXT, TPM,
# linux (or anything) on the
okL4 verified microvisor
# and using Joanna's system of
5 vm's for each security domain,
-- or [Joanna's Qubes]("http://theinvisiblethings.blogspot.com/2010/10/qubes-alpha-3.html")

**5 vm's for each security level:**
# red: browsing random sites, no privacy;
-- expected to get infected;
. I revert it to a known snapshot every week or so.
# yellow: semi-sensitive tasks,
. uses firefox.NoScript to only allow
 scripting to a trusted few sites:
  online shopping, blogging, etc.
Sure, somebody might do a
 man-in-the-middle (MITM) attack against
a plaintext HTTP connection
that is whitelisted by NoScript
and inject some malicious drive-by exploit,
but then again,
Yellow machine is only semi-sensitive
and there would not be a big tragedy
if somebody stole the information from it.
[unless credit cards are used?
maybe that's for green vm?]
# green:  https-only, bank's account
. it is quite important to make sure
only HTTPS is used for this machine
to mitigate potential MITM attacks;
for example, on any hotel Wi-Fi.
.  don't use the host's browser as a Green machine:
[the host is a huge attack vector;
and, all the attacks are coming from online;
so, take it offline .]
# [where to keep one's email client:]("http://qubes-os.org/Architecture.html")
[with separate personal and work vm's;
both have mozilla mail;
work needs a noscript browser]

**other tips:**
#handling updates:
[getting prompt updates for each guest vm
dramatically reduces the number of attacks .]
# clipboard:
[every guest can be logging the clipboard .]
transfer of files between vm's and host:
[more networking is more risk .]

The advice is good but considering alot of that stuff you talked about relates to a blogger account I think it's some kind of nulled app to get hype.

---

