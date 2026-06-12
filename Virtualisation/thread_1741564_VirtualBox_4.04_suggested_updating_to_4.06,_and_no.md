---
title: "VirtualBox 4.04 suggested updating to 4.06, and now VirtualBox won't run at all"
date: 2011-04-28
forum: Virtualisation
---

### Post by rewyllys on 2011-04-28
I'm running Maverick on an IBM Thinkpad T42, with Ubuntu as the only OS on this laptop.

After several months of using VirtualBox 3.2.8, for the last two weeks I've been running VirtualBox 4.04.  About 3 hours ago I opened VBox and saw its report that v. 4.06 was available. So I tried to install 4.06, using Ubuntu Software Center, and that update failed. 

I've tried all kinds of things since then to try to recover, but without success.  The last thing I tried was clearing out all traces of v. 4 and going back to v. 3.2.8 via Synaptic Package Manager.  Even this has failed, yielding the following VirtualBox Error report:
> Failed to open a session for the virtual machine LaptopVirtualXP2
Unsupported version 13 of data unit 'pgm' (instance #1 pass
0xffffffff)(VERR_SSM UNSUPPORTED_DATA_UNIT_VERSION).

Result Code:   NS_ERROR_FAILURE (0x80004005)
Component:     Console
Interface:     IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}
At this point I decided to ask here for help.  Any and all suggestions will be much appreciated.

I'd like to get back to VirtualBox 4.04, which was running distinctly faster than v. 3.2.8, or to get 4.06 working, if it is free of bugs.  But I'd settle for a workable v. 3.2.8.

---

### Post by CharlesA on 2011-04-28
Do you have any snapshots?

---

### Post by rewyllys on 2011-05-04
> **CharlesA said:**
> Do you have any snapshots?
CharlesA,
Many thanks for your quick response, together with my apologies for responding to you so slowly. In the intervening time I've unfortunately had a number of more serious distractions.

Here's the error message that VirtualBox 3.2.8 delivers when I try to open Windows XP in it:
>                                        Failed to open a session for the virtual machine **LaptopVirtualXP2**.
 Unsupported version 13 of data unit **'pgm'** (instance #1, pass 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION).
 Details
 

                                      Result Code:              
                               [FONT=Courier New,courier]NS_ERROR_FAILURE (0x80004005)[/FONT]
                                         Component:              
                               Console
                                         Interface:              
                               IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}
                

 

---

### Post by CharlesA on 2011-05-04
I meant snapshots of the VM.

Most of the solutions I found had something to do with deleting any snapshots you had of that VM.

[http://www.google.com/search?q=VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by rewyllys on 2011-05-04
I'm sorry, but I'm not sure what you mean by "snapshots of the VM."

---

### Post by CharlesA on 2011-05-04
> **rewyllys said:**
> I'm sorry, but I'm not sure what you mean by "snapshots of the VM."

I mean these:

---

### Post by rewyllys on 2011-05-04
Thanks for your continuing readiness to help me.  I just tried to post a snapshot, but failed somehow to be able to do so.

Meanwhile, I've pretty much finished a successful trial installation of Ubuntu 11.04 on my desktop, and I've found that it has VirtualBox 4.04 available via Synaptic Package Manager. 

Since I've now got VBox 4.04 running in both 10.10 and 11.04 on my multiple-boot desktop, it's become clear that the sensible solution to VBox's current problem on my laptop is for me to upgrade to Natty on the laptop and re-install VBox 4.04 therein.  I plan to do so shortly.

Thanks again for your help.

---

### Post by Bazon on 2012-04-18
I had the same problem (only with newer vb versions), for me the following helped:
rightclick on virtual machine in virtualbox, select "Verwerfen" (STRG+J) *[I suppose "discard" (CTRL+J) or something like that in english]*.
Next time, the virtual machine booted from bios and everything went fine. :-)

---

