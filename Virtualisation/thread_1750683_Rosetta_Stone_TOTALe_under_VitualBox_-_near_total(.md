---
title: "Rosetta Stone TOTALe under VitualBox - near total(e) success"
date: 2011-05-05
forum: Virtualisation
---

### Post by Samloops on 2011-05-05
Hi Everyone,

I was able to install Rosetta Stone V.4 Russian in an XP sp3 VBox 4.0.6 guest under Ubuntu 10.10 without significant issues using the version from Oracle with USB support. The install even survived a rather horrible upgrade to 11.04.  The program runs quite well on what I can think is rather minimal equipment... a 2.4 GHz P4.  The sound is slightly broken using the supplied USB headset but maxing out the memory allotted to the guest (1.5 MB in my case) seems to help.

Pushing my luck, however, I signed up for a live Studio session with a native speaker.  That didn't work at all.  It was all rather embarrassing to sit there dumbstruck as she was asking me (in Russian of course) to identify what I was seeing.  Well, it took me a while to figure out that I was supposed to be seeing some pictures on the screen.  And I wasn't.  The program was acting as though it was really struggling or locking up. Eventually, I did see a picture but it disappeared.  I could even see her in a webcam window for second or two before that would disappear as well.  After much struggling, I got across to her in bastardized Russian that I wasn't seeing anything and gratefully got passed off to tech support where I did get some hints (in English).

1) The Studio session is essentially a Flash session and so Adobe Air installs with the program, and
2) Upload and download speeds need to be minimum 768 kbps.

Running Rosetta Stone's speed test at speedtest.trstone.com suggests that my download speeds are sufficient but upload speeds are not, capping out at 475 kbps. Speeds are the same whether I test from a browser running under VBox or outside in Ubuntu. I am suspicious that this is not the issue, however.

I've noticed that while Rosetta Stone is doing nothing more than idling at the program's main menu, it is consuming upwards of 70% of the CPU.  I believe that is the real issue and so therein lies my question.  Any ideas about where I can find the problem?

I've called up a YouTube video, right-clicked on one and modified some of the Flash Global Settings.  I've provided Flash with additional disk space, etc., but didn't see anything that would really help... and nothing did.  I've looked via Task Manager at background processes running in XP and though there are a crapload of them, I don't see anything that is consuming the CPU.  When I close out Rosetta Stone, CPU consumption drops to near zero and so it is definitely that program.  

Anybody else seen something that consumed inordinate amounts of CPU under VBox and found a fix?  Anywhere else I can tweak Flash or Air?  Rosetta tech says that they are not aware of any conflicts but of course say that they don't support running in a virtualized environment.  He suggested running under wine, but checking winehq, version 3 of Rosetta Stone gets a Platinum rating, but version 4 rates a "garbage".  So guess that's not an option. 

Thanks in advance...

---

### Post by tfbielawski on 2011-06-05
Thanks for the tip on using Virtual Box. I have been struggling with WINE. 

Sorry, I have no suggestions for your other issues.

TB

---

### Post by Samloops on 2011-12-30
Just an interesting update to the Rosetta Stone Totale installation under 11.04... I happened to swap out the Rosetta Stone headset for a cheap gaming version.  The Rosetta Stone headset is recognized as a VOIP device when viewed under System > Preferences > Sound > Hardware in Ubuntu, but the new headset is recognized as an "Audio Adapter".  If I select "Audio Adapter" under the Hardware, Input and Output tabs, then fire up VirtualBox, boot Windows and call up Rosetta Stone, the sound is great! No breaking of the audio, even at the Windows boot screen.  The trick is to make sure that the proper audio hardware is selected in Ubuntu before the hardware is grabbed by VirtualBox.

Still haven't resolved the high CPU usage issue.

---

