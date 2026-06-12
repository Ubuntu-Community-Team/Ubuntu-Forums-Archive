---
title: "Vista EULA to prohibit running Vista in a Virtual Machine"
date: 2006-10-12
forum: Windows
---

### Post by Dr. C on 2006-10-12
The following is from article in Information Week 

" Microsoft Makes Vista Licensing Tougher On Users
New licensing restrictions on retail versions of Vista say users can only transfer licenses between PCs once. They also forbid users from running Vista on virtual machines. "

[http://www.informationweek.com/news/showArticle.jhtml?articleID=193300292&subSection=Breaking+News]("http://www.informationweek.com/news/showArticle.jhtml?articleID=193300292&subSection=Breaking+News")

What is Microsoft afraid of if they put this in their EULA?

---

### Post by koshari on 2006-10-12
> What is Microsoft afraid of if they put this in their EULA?

has anyone ever read one of these EULA things?

---

### Post by meng on 2006-10-12
Yawn - whatever Microsoft wants to stipulate to restrict usage of their OS is their own business. Who am I to argue? It doesn't make business sense to me, but given their current marketshare, they'd have to do quite a lot wrong to run into trouble.

---

### Post by bruenig on 2006-10-12
Unenforcable

---

### Post by Shay Stephens on 2006-10-12
They have lost their mind.  They are in a paranoia spiral.  Glad I got off their bus because its heading toward that cliff over there ;-)

---

### Post by Dr. C on 2006-10-13
It is actually very easy to enforce. 

To block virtualization all they have do is detect the virtualized bios and hardware from a handful of products, VMWare, BOCHS etc, and their own virtual server and block them at activation time. If they find a that a particular hardware setup is virtualized after activation then they can always revoke the key after the fact. 

To block more than one change of computer is very simple: Allow only two activations per key with substantially different hardware. 

I do agree it does look to me that their bus is heading for that cliff over there, but their bus has first to climb a very high mountain so it will take quite some time before their bus gets to the cliff.

---

### Post by ago on 2006-10-13
If they are pushing so hard with restrictions, it means that they are CONVINCED that users have no alternatives and will not switch anyway. I am not sure whether I should be concerned or happy about their perception....

---

### Post by Magnes on 2006-10-13
I read an EULA once for MSDNAA programs. I'm not shure if I can use notepad from MSDNAA (free for some students) WinXP to write public html page without violating that licence. It's stupid. :)

---

### Post by ade234uk on 2006-10-13
Just let Microsoft keep digging deeper holes for themselfs. It's all the more reason to use Linux at the end of the day. 

Mr & Mrs Brown will always keep Windows and think it is great whatever M$ do, but there are going to be companies and computer savey people that can see what is going on and may be just may be make the switch.

In my opinion it seems to me M$ are slowly locking everything down way too much.

What next? 

You can only use Microsoft's search engine to search the web!

You can only use websites if they are approved by Microsoft.

I know the above thoughts are stupid but I would not anything past M$.

Microsoft are losing share everyday from Apple and Linux. I dont think M$ profits will grow like they have before.

---

### Post by BLTicklemonster on 2006-10-13
What if:

what if the majority of the people on the planet who use pcs, the ones who just browse the internet, listen to music, chat with friends, view emails, etc; what if they suddenly all realized that they DID NOT NEED MICROSOFT in order to use their computers? What if this large demographic were to learn of an alternative that was free, and when a new version came out the didn't have to fork out another hundred bucks, could put it on as many machines as the wanted, etc. What would happen to Monopolysoft then?


Spread the word, people. Ubuntu-automatix or easy ubuntu- bam, no more windows.

---

### Post by anaconda on 2006-10-13
Intersting, because here in Finland there was a discussion of the legality of EULA, and the result was that the EULA is not legally valid unless you have to sign it when you purchase windows...  

And havn't head they make anyone sign the eula.. (yet)

another thing is that if you just cant activate the vista in VMWare or elsewhere where EULA prohibits its use..

---

### Post by Pluk on 2006-10-13
This is not true. 

Microsoft doesnt allow the installed windows vista license to be used in a virtual machine on the same computer, however it does allow it with vista ultimate.

So to use windows vista in a virtual machine you either have to use a different license then the one installed on your pc, or you have to have windows vista ultimate.

---

### Post by blastus on 2006-10-13
The only thing that can be said about commercial software licenses, is that in general they are becoming more and more restrictive by stripping more and more rights or privileges or whatever you want to call it from people that have paid for the software. 

Buying software means nothing today. The world is sold on the idea that a license can legitimately and legally contain anything and we are supposed to accept it (or reject it.) We aren't supposed to complain because well, the company owns the software and therefore they can dictate absolutely anything about the way their software is used.

What's next? Who knows. Maybe you can't install Windows on a machine that has Linux or some other non-MS OS on it. Or maybe you can't use Windows if your cat can use a keyboard or likes playing with your mouse.

---

### Post by Dr. C on 2006-10-13
> **Pluk said:**
> This is not true. 

Microsoft doesnt allow the installed windows vista license to be used in a virtual machine on the same computer, however it does allow it with vista ultimate.

So to use windows vista in a virtual machine you either have to use a different license then the one installed on your pc, or you have to have windows vista ultimate.

For the home basic and home premium versions of Vista this is the relevant language 

"USE WITH VIRTUALIZATION TECHNOLOGIES. You may not use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system."

For the Ultimate Version of Vista this is the relevant language 

"USE WITH VIRTUALIZATION TECHNOLOGIES. You may use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system on the licensed device. If you do so, you may not play or access content or use applications protected by any Microsoft digital, information or enterprise rights management technology or other Microsoft rights management services or use BitLocker. We advise against playing or accessing content or using applications protected by other digital, information or enterprise rights management technology or other rights management services or using full volume disk drive encryption."

The EULA is silent on what happens if the Software has not been installed on the licensed device other than in the "virtual (or otherwise emulated) hardware system on the licensed device." I believe that ambiguity in a contract cannot benefit that party that drafted the contract so it may turn out when it comes to virtualization this EULA may not be as draconian as it first appears.  

The EULA can be found here on the Microsoft site

[http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_9d10381d-6fa8-47c7-83b0-c53f722371fa.pdf]("http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_9d10381d-6fa8-47c7-83b0-c53f722371fa.pdf")

---

### Post by linbetwin on 2006-10-13
XP's EULA stipulates the same interdiction, as I recall.

---

### Post by Dr. C on 2006-10-15
XP's EULA is silent on the subject of virtual machines and does not limit the transfer of the software from one computer to another except for OEM versions.

[http://download.microsoft.com/documents/useterms/Windows XP_Professional_English_9e8a2f82-c320-4301-869f-839a853868a1.pdf]("http://download.microsoft.com/documents/useterms/Windows XP_Professional_English_9e8a2f82-c320-4301-869f-839a853868a1.pdf")

---

### Post by blastus on 2006-10-15
[quote=FineE]XP's EULA is silent on the subject of virtual machines and does not limit the transfer of the software from one computer to another except for OEM versions.

[http://download.microsoft.com/docume...9a853868a1.pdf](http://download.microsoft.com/docume...9a853868a1.pdf)[/quote]

Paul Thurrott recently wrote an article about this: [Licensing Changes to Windows Vista](http://www.winsupersite.com/showcase/winvista_licensing.asp)

He claims that there has been no change in the license between XP and Vista regarding transfers. And his reasons seem to be that Windows is licensed to a device not a person and because Microsoft never intended infinite transfers.

First, the fact that Windows is licensed to a "device" and not a "person" seems irrelevant to whether the license can be actually transferred from one thing to another and how many times it can be transferred. There is a difference between a device and a person, but there is nothing inherent in the fact that Windows is licensed to a "device" instead of a "person" or vice versa that says one can only transfer the license once. It is reasonable to expect the license would say something about such a transfer restriction if it indeed existed.

Second, even though he admits the license does not explicitly explain how many times one might transfer a single copy of XP, he seems to think that just because Microsoft intended that there should be only one transfer between devices that that is the way it is. This must not have been an important enough restriction to Microsoft otherwise they would have included it in the license. Obviously people are not going to assume that such a basic restriction exists simply because Microsoft intended for it to exist. If that were the case then we can extrapolate basically anything not in and not contradictory to the license on the sole basis that well, that is what Microsoft intended when they framed the license.

---

### Post by Dr. C on 2006-10-15
Paul Thurrott's reasoning is flawed. The license for Windows XP per device as opposed to per person is to prevent the same person installing and using the same license on Windows XP on multiple computers at the **same time**. It has nothing to do with transfers. 

The motivation for this change has to do with product activation. If you allow infinite transfers then you have to allow infinite activations on different hardware, and Microsoft has no way of knowing if the software was deleted from the "old" computer each time short of sending out an auditor. So the EULA has to be “clarified” read restricted in order not to make product activation a farce. By the way what Microsoft says they intended when they drafted the EULA is not the point. What matters in the actual legal wording in the EULA. 

As for the prohibition on running certain versions of Vista in a Virtual Machine, I can see something else. The primary motivation for a home or small business user to run Windows in a VM as a guest is if they have recently migrated to Linux, and need backward compatibility with some Windows applications. So Microsoft is trying to be the host rather than the guest seeing the host as the point of control.  I find it interesting that the only combination where VMware supports accelerated 3-D is with a Linux host and a Windows guest. Paul Thurrott again fails to see the reason behind Microsoft's change in the EULA from XP to Vista

---

### Post by turkenator on 2006-11-02
it looks like microsoft is going to loose some power users and techies with the new MS LAWS but they wont loose that much blood as long as pc's continued to be pumped out with vista pre installed

---

### Post by Shay Stephens on 2006-11-02
> **turkenator said:**
> it looks like microsoft is going to loose some power users and techies with the new MS LAWS but they wont loose that much blood as long as pc's continued to be pumped out with vista pre installed

But...what happens when those power users start demanding PC's that are *not* preloaded with windows.  Companies do listen, uninformed people do listen to recommendations for power users.  It's a two way street.  You can't have an exodus without it having an impact.  The next year or two should be interesting.

I have personally contacted my hardware vendor, and they have agreed to supply me with PC's that are not preloaded with Windows.  You get enough of those kinds of requests, and well...

---

### Post by trash on 2006-11-02
the market share makes it so they don't have to worry about what a few thousand users think... Apple is living proof of that, when they wouldn't allow first generation bug ridden OSX users upgrade for free or even a discount... apple lost a lot of dedicated users over this and they did not give a hoot.

---

