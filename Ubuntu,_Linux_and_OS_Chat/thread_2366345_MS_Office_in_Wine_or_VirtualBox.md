---
title: "MS Office in Wine or VirtualBox?"
date: 2017-07-16
forum: Ubuntu, Linux and OS Chat
---

### Post by russkyca on 2017-07-16
I need to use Word and Excel (for both casual use - people who use Windows and for work - soon).

I can dual boot but I don't have a SSD yet - when I get a SSD, how fast will be compared to using Ubuntu 17.04 and either using Wine or Virtualbox?

I'm a little familiar with VirtualBox.   Wine, I haven't used much.   I suppose this has been asked before but Wine versions are more up to date and I guess Wine developers are changing things (for the better, I hope) and hopefully, it's improving.   I read old(er) messages - not necessarily this forum - that there have been bugs or glitches when using Wine.   That might be mostly regarding games, though.

I guess the question(s) are:
1) Should I just dual boot for this
2) Should I use Wine for this
3) Should I use Virtualbox for this
 
Will I run into trouble if I try both or all 3?   I guess I don't need to install Windows to use the Wine method - right?   But, if I want to compare dual-booting and VirtualBox, I'd have to install Windows twice - I'd need two copies of Windows?

I plan on using Windows 10.   

I am currently (at the moment) using Ubuntu 17.04.   Let me know if I need to provide further info, thanks.

I don't think it matters which version of Office I am using for this task - or does it?   

Thanks for any replies - in advance.

---

### Post by monkeybrain20122 on 2017-07-16
> **russkyca said:**
> I need to use Word and Excel (for both casual use - people who use Windows and for work - soon).


If you only use them casually why can't you just use LibreOffice??

---

### Post by wildmanne39 on 2017-07-16
I would just use virtualbox, it works well, but I would stay away from using wine.

---

### Post by wildmanne39 on 2017-07-16
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by mastablasta on 2017-07-17
> **russkyca said:**
> 
I don't think it matters which version of Office I am using for this task - or does it?   


yes, it matters a lot. 

Office 2010 and 2007 (possibly even 2013) are relatively well supported by Wine. the thing that can crash it all is smart art. it also depends which programs because word, excell and powerpoint are well supported. Access and a few others not as much.

it also matters becausse if your work has office 365 or 2016 then you can access your work via browser from anywhere and from any OS (including files stored in one drive and such). sure, the browser based editors are a bit more basic and but they are more than enough to do the job.

wine is a compatibility layer that helps run windows programs in linux. it basically tricks them into thinking they are running in windows and that all is well.

virtualbox should be faster than dualbooting because you can restore session from snapshot.

dualboot on SSD will be fast, but you may get into troubles as windows 10 likes to take over the PC with upgrades/updates and you do need to turn off the default windows 10 behavior (hybernation of sorts), which means it will be cold boot and it (the boot) will be longer than if you just had windows 10 installed.

so, think about this:
- if it is only office that you need what part from the office you need?
- do you need maybe windows for your work? if so then by all means you should install it.
- what kind of office will they use at work? if it is 365 or similar, then maybe you do not need to install anything at home.
- in terms of launch speed: wine > virtualbox (or other VM) > dual boot
- in terms of least problems with windows based apps: dual boot > virtualbox (or other VM) > wine

---

### Post by ardouronerous on 2017-07-17
> **monkeybrain20122 said:**
> If you only use them casually why can't you just use LibreOffice??

Based off my experience, LibreOffice Writer and MS Word don't play nice with each other, especially with .docx files, for example, when my lawyer sent me legal documents saved in .docx to print and sign, the documents didn't come out right in LibreOffice Writer, so I had to edit the documents to make them look presentable for printing, a pain in the ass to do.

---

### Post by monkeybrain20122 on 2017-07-17
> **ardouronerous said:**
> Based off my experience, LibreOffice Writer and MS Word don't play nice with each other, especially with .docx files, for example, when my lawyer sent me legal documents saved in .docx to print and sign, the documents didn't come out right in LibreOffice Writer, so I had to edit the documents to make them look presentable for printing, a pain in the ass to do.

Not in my experience. At work they send me docx and xslx and I open just fine. OP said he is a casual user so IMO there is no need for MSO until he runs into problems.

---

### Post by HermanAB on 2017-07-17
Windows 10 is verrry slow in a virtual machine.  To use it, you need to disable a lot of stuff, effectively turning it into Windows 7, so you can just as well install Windows 7 and save yourself the hassle.

---

### Post by ardouronerous on 2017-07-17
> **monkeybrain20122 said:**
> Not in my experience. At work they send me docx and xslx and I open just fine. OP said he is a casual user so IMO there is no need for MSO until he runs into problems.

Are you sure the .docx files comes out okay? No paragraphs misaligned or anything?

Because this user claims to have problems similar to mine: [https://ask.libreoffice.org/en/question/2676/when-i-open-a-docx-file-it-does-not-format-correctly-is-there-a-way-to-make-it-format-easily/](https://ask.libreoffice.org/en/question/2676/when-i-open-a-docx-file-it-does-not-format-correctly-is-there-a-way-to-make-it-format-easily/)

---

### Post by vasa1 on 2017-07-17
> **ardouronerous said:**
> .., when my lawyer sent me legal documents saved in .docx to print and sign, ...
Sending files in pdf format would be more conveninet.

---

### Post by ardouronerous on 2017-07-17
> **vasa1 said:**
> Sending files in pdf format would be more conveninet.

Not always convenient, especially when you see an error on the PDF file and wish to correct it.

---

### Post by montag dp on 2017-07-17
> **monkeybrain20122 said:**
> Not in my experience. At work they send me docx and xslx and I open just fine. OP said he is a casual user so IMO there is no need for MSO until he runs into problems.Opening them is fine if you just want to read them, but not if you want to edit them and have them come out with the same formatting in MS Office.

My opinion: give wine a try first. It has worked pretty well for me in the past with Word, Excel, and Powerpoint (with the one exception being that I could never get videos to work right in Powerpoint). VirtualBox will definitely work, but then you need to deal with the hassle and overhead of running a Windows VM (slow updates, big chunk of hard drive space reserved, etc.).

---

### Post by vasa1 on 2017-07-17
> **ardouronerous said:**
> Not always convenient, especially when you see an error on the PDF file and wish to correct it.That's partly the aim of pdf's: to prevent the recipient from altering them ;)

Of course, if there are lawyers comfortable with clients altering their files, that's fine then.

---

### Post by monkeybrain20122 on 2017-07-17
> **ardouronerous said:**
> Are you sure the .docx files comes out okay? No paragraphs misaligned or anything?

Because this user claims to have problems similar to mine: [https://ask.libreoffice.org/en/question/2676/when-i-open-a-docx-file-it-does-not-format-correctly-is-there-a-way-to-make-it-format-easily/](https://ask.libreoffice.org/en/question/2676/when-i-open-a-docx-file-it-does-not-format-correctly-is-there-a-way-to-make-it-format-easily/)


None. But then I don't have exotically formatted docx files and my LO is always up to date.

---

### Post by monkeybrain20122 on 2017-07-17
> **montag dp said:**
> Opening them is fine if you just want to read them, but not if you want to edit them and have them come out with the same formatting in MS Office.


That depends on what OP means by "casual user". If you do a lot of editing and going back and forth it may not fall into my definition of that. I have to only do some small editing on not very complicated documents and never had a problem. Now I basically send them out in .odf if I write something or output something from scratch. MSO is supposed to work with that as they claim. No one has complained. 

Also, some people use Office only for personal (non business related) purposes and they don't really have to use MSO's formats. Why perpetuate closed formats unnecessarily? For things like resume you can always print to pdf.

---

### Post by montag dp on 2017-07-17
I agree about closed formats. I don't use MS Office at all anymore, except at work. Whether that's a good solution for the OP depends on what he means by "casual user," as you said. In my experience, you don't need to do heavy editing to have formatting issues going back and forth. The same is true for going back and forth between different versions of Office, too.

---

### Post by pmorch on 2018-06-24
And just for reference. While Office 2007 and 2010 also in my experience work fine under wine (I prefer to use PlayOnLinux or the non-free CrossOver office), you cannot legally purchase licenses for Office 2007 or Office 2010 any longer. :-( Sure, you can find them on eBay from some company in Timbuktu, but that doesn't make them legal.

And I have to say: Sure if you have very simple documents, LibreOffice will be ok. If you stick to LibreOffice .odt files, you'll be OK. But if you want to edit documents as part of a professional team where all the others are using MS Office, and some of the documents are non-trivial (e.g. 100-page word documents with lots of images formatted just-so, tables, fields), LibreOffice is going to mess up these documents. Sorry. I wish it wasn't so. My milage with Office 365 in the browser also varied, and I also saw Office 365 mess up non-trivial documents.

So your only alternative is Virtualization or remote desktop (or both). I use VirtualBox and Windows 10. Seamless mode makes you think that you can run e.g. Word almost as if it is a Linux program until you discover that [Seemless mode doesn't work with Windows 10]("https://www.google.com/search?q=virtualbox+seamless+mode+windows+10").

In our team, we've gone all-in with LibreOffice (and Markdown), but for the wider company, it is Windows and Office on a virtual machine, which is a pain in the a.. .

---

