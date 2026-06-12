---
title: "Has your System76 Meerkat been Bricked by Suspend?"
date: 2015-12-20
forum: System76 Support
---

### Post by dalinian on 2015-12-20
***Hi System76ers,***

The  System76 Meerkat is a rebadged Intel NUC, and many Intel NUC users have  reported that the Linux Suspend command intermittently bricks their  computer (within multiple complaint threads in the communities.intel.com  forums). Now two System76 customers are reporting that their Meerkats  have been bricked by Ubuntu Suspend [1], too.

If your  System76 Meerkat has also been bricked after using Ubuntu Suspend,  please share your experiences by posting a reply below, so that we can  build up a picture of how widespread this problem is.[INDENT][I]
"**We are working on this behavior, hopefully we will have a solution[COLOR=#ff0000] soon.[/COLOR]**

We  noted some compatible issues between our NUCs and some Linux flavors.  It is hard to provide support with each distro. I would appreciate if  you can reply with the kernel version, BIOS version and customized  settings that you are using. If you are using a customized kernel,  please send a copy of it (ISO); you can send it as a private message or  use dropbox or any other method."[/I]
~ Mike C., Intel technical support, 18 Dec 2015
[/INDENT]

Since  some of the first reports of the 'Linux Suspend > Dead NUC' problem  date back a year [2], Mike's "***[COLOR=#ff0000]soon[/COLOR]***" may very well vary somewhat from its  colloquial meaning. ;)

Nevertheless, if  you'd like to assist Intel in  developing a solution, please post the Linux version data requested by  Mike as a reply to his post #6 here » [https://communities.intel.com/message/360520#360520](https://communities.intel.com/message/360520#360520) (for an example, see post #8 it that thread).

[I][B]Thanks in advance for helping to raise awareness of this problem,
[/B][/I]
***Tim Jones***

__________________________________________________________________ 

[1] Two System76 customers are reporting that their Meerkats have been bricked by Ubuntu Suspend:
&#8226; Dalinian (Tim Jones, OP) and nikitas in 'NUC5i5RYH Bricked by Ubuntu Suspend for Fifth Time'
» [https://communities.intel.com/thread/96168](https://communities.intel.com/thread/96168) 
...from which comes the following defective Meerkat failure mode details:
[LIST]
[*][I]"The well-known 'Ubuntu Suspend > Dead NUC' problem:
[/I]
[LIST]
[*][I]Mean time between failures: 10.8 days (5 failures in 54 days of use, in my personal experience).
[/I] 
[*][I]Symptoms #1: each use of the Ubuntu Suspend function carries a small  but real risk of bricking the NUC. When Ubuntu Suspend is used and works  normally, the NUC goes into sleep mode, and the Power button LED winks  amber. When the 'Ubuntu Suspend > Dead NUC' problem occurs, these are  the symptoms which afflict sleep mode:
[/I]
[LIST]
[*][I]a short press on the Power  button does not wake the NUC (as it ought to, and usually does) &#8211; the  amber winking just continues; and
[/I] 
[*][I]a long press on the Power button  does not switch the NUC off (as it ought to, and usually does) &#8211; the  amber winking just continues.
[/I] 
[/LIST]
  
[*][I]Symptoms #2: the only way to get the  NUC to power off is by disconnecting the power cable. After the power  cable is reconnected:
[/I]
[LIST]
[*][I]a short press on the Power button does not switch the NUC on (as it ought to, and usually does) &#8211; the NUC is bricked; and
[/I] 
[*][I]a long press on the Power button does not start the NUC up in Power  Button Menu mode (as it ought to, and usually does) &#8211; the NUC is  bricked.
[/I] 
[/LIST]
  
[*][I]Workaround: to get my NUC to work again, I have to fully  disassemble the NUC, disconnect and reconnect the CMOS battery from the  motherboard, and reassemble the NUC.
[/I] 
[*]*Users of Linux distributions  other than Ubuntu (eg: Arch Linux, Fedora) have also reported  experiencing this NUC bricking on using Suspend, so it could be  described more inclusively as the 'Linux Suspend > Dead NUC'  problem."* 
[/LIST]
      
[/LIST]
[2] The first reports of the 'Linux Suspend > Dead NUC' problem date back a year &#8211; for example, see: 
&#8226; 'NUC dead after suspend mode in Ubuntu 14.10', from 23-Dec-2014 
» [https://communities.intel.com/message/270395](https://communities.intel.com/message/270395)

---

### Post by dalinian on 2015-12-20
I'm the OP of both this thread and the 'NUC5i5RYH Bricked by Ubuntu Suspend for Fifth Time' thread at the Intel NUC forums.

My  Meerkat was bricked for the sixth time with System76's BIOS Update  v.0350 installed. This was delivered as BIOS updater file  'meer1-0350.bio' by System76 tech support person Mark, who led me to  believe that it fixed the 'Ubuntu Suspend > Dead Meerkat' problem –  but later, after repeated questioning, admitted *"We have not modifies *[sic]* the suspending routine in the release we have."* (My Meerkat was also bricked, for the fourth time, with Intel's BIOS Update v.0350 installed.)

So  my experience is that no fix yet exists –  all of the five suggested  fixes (including Intel's and System76's v.0350 BIOS Updates) which I've  implemented fail to eliminate the  'Ubuntu Suspend > Dead Meerkat'  defect. Intel's own Mike C. says *"**We are working on this behavior, hopefully we will have a solution [COLOR=#ff0000]soon[/COLOR]**,"* so Intel knows full well that they've not yet fixed their underlying  'Linux Suspend > Dead NUC' problem.

Meanwhile,  when a potential new System76 customer enquires about the 'Linux  Suspend > Dead NUC' problem with regard to buying a new Meerkat  computer, she's told:[INDENT][I]
"**The  suspend issue is definitely not a concern on our current units.** We ship  with v.0350 and it works. **The bios fix** was implemented at the end of  November and it **did resolve the suspend issue**. We wouldn't be selling it  if it were still an issue. We do different development once we receive  our products and still do  not have any issues with the suspend feature since the new Bios was  implemented. We don't speak for Intel, so if they don't have a  fix, that's on them."[/I]
~ Emma, System76 saleswoman
[/INDENT]
  
So  it's looking very much like System76 are willing to deceive potential  new customers that all's well, for the sake of unloading Meerkats which  are still just as likely to express  the  'Ubuntu Suspend > Dead Meerkat'  defect. 

Since I detailed my litany of failed remedies in the Intel forums, System76 tech support person Mark says *"We're thinking at this point that there may be something odd *[sic]* going on with your unit,"*  and has sent returns documents for shipping my defective Meerkat back  to their Denver HQ; I'm negotiating for a replacement prior to return,  and if Meerkat #2 proves to be equally defective, then a full refund.

---

### Post by dalinian on 2015-12-20
FYI, 'Ubuntu Suspend > Dead Meerkat' defect report #2, on a similar Meerkat :[INDENT][I]
"Hi all,[/I]

*I  just wanted to add I have the EXACT same issue with the initiator of  this thread. Same Meerkat, ubuntu version, BIOS version etc. I got it  end of September and ran into the suspend > brick issue about a week  after that.*

*I did  contact System76 once I did the CMOS trick (what a pain), and I also got  the "This is new to us" story and I'm yet to hear anything back. What's  certain here is that System 76 are indeed lying to their customers.*

***@Mike:** I also appreciate your response and looking forward to seeing this issue fixed.*


*nik"*

~ Meerkat user nikitas, 18 Dec 2015
&#8211; source » [https://communities.intel.com/message/360663#360663](https://communities.intel.com/message/360663#360663)
[/INDENT]

---

