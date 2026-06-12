---
title: "Legal MP3 Encoding in USA with Linux?"
date: 2005-10-02
forum: The Cafe
---

### Post by sb73542 on 2005-10-02
Hello,

I am trying to set up a digital recording solution for a non-profit organization.  I would like to use Linux because Windows costs too much.  But I need to be able to encode some of the organization's **original** content to MP3 audio, so that it will work with people's MP3 players.  I'd use Ogg if I could, but our end consumers are not techy individuals, and very few players support Ogg.

It's imperative that I use software that is 100% free of legal issues in the USA.  I can't use anything shady or for which there exists even the possibility of legal trouble in the event of a government audit, etc.  Is there any existing software that I can legally use?  Or would it be possible for me to use LAME, after paying the MP3licensing company their $0.75?  Or do they only license to big companies in volume?  Does anyone know if it's genuinely legal to encode MP3 using Windows out of the box?

I'm not concerned at all with the principles of OSS- I personally use Java and Flash, etc. because they are perfectly legal and absolutely necessary.  I'm confused about Ubuntu's stance on MP3's, whether they are eliminating official support because of OSS sentiments or because it's truly illegal in some areas.

Thanks for your help!

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=sb73542]Hello,
I am trying to set up a digital recording solution for a non-profit organization.  I would like to use Linux because Windows costs too much.  But I need to be able to encode some of the organization's **original** content to MP3 audio, so that it will work with people's MP3 players.  I'd use Ogg if I could, but our end consumers are not techy individuals, and very few players support Ogg.
It's imperative that I use software that is 100% free of legal issues in the USA.  I can't use anything shady or for which there exists even the possibility of legal trouble in the event of a government audit, etc.  Is there any existing software that I can legally use?  Or would it be possible for me to use LAME, after paying the MP3licensing company their $0.75?  Or do they only license to big companies in volume? [/QUOTE]

You can't just buy a single license I don't think. The only legal MP3 player in Linux is the Realplayer, maybe it encodes MP3s. I don't know.


  > I'm confused about Ubuntu's stance on MP3's, whether they are eliminating official support because of OSS sentiments or because it's truly illegal in some areas.


Then let this page explain:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
> 
Below is the reason why Ubuntu lacks media support for closed codecs "out of the box."

A single example will be used- MP3's.

The group that holds the patent on MP3's demands that for each player with MP3 support a 75 cent fee must be paid:

[WWW] [http://www.mp3licensing.com/royalty/index.html](http://www.mp3licensing.com/royalty/index.html)

It might not seem like a lot, but when the distro is free then even such a small fee is too much. The only other option is to pay a large one time fee that could otherwise pay a developer to work on Ubuntu for a whole year! So it costs money to distribute software that pays MP3s.

If Ubuntu ignored this, it could be sued in nations like the U.S. where this patent is valid. Either Ubuntu would have to pay up or the developers could never set foot in a country with such patent laws ever again (not reasonable). So because it costs money, Ubuntu has no MP3 support.

Now take this situation, and multiply it times every type of restricted software out there (that isn't a free like OGG) and you see what the situation is. So in order to spend money on developers, not laywers, Ubuntu has to avoid touching these codecs. Even an easier way to install them such as "click here to install" would make Ubuntu an accessory to a crime in many nations.

This is why its important to support open codecs and standards. But Ubuntu can't provide restricted software, or make it any easier because of the law.


---

### Post by sb73542 on 2005-10-02
Thanks for your fast reply!

Hmmm.  I almost positive that Realplayer doesn't encode anything.  It only plays.

I guess I could just use Windows.  Anyone know if it's legal with a default Windows install?  Thanks!

---

### Post by sb73542 on 2005-10-02
Huh, what do you make of this?

[http://www.mp3licensing.com/help/#5](http://www.mp3licensing.com/help/#5)
> However, no license is needed for private, non-commercial activities (e.g., home-entertainment, receiving broadcasts and creating a personal music library), not generating revenue or other consideration of any kind or for entities with associated gross revenue less than US$ 100 000.00.

Does this apply if I'm using LAME or some other OSS encoder that hasn't payed anyone any royalties?  And what about a non-profit (and low income too) organization?  The MP3's are absolutely not being sold, but it's not exactly a private user...

---

### Post by Kyral on 2005-10-02
Hold up. I thought that the guy who patented the MP3 format could only get away with charging for something that "generated an MP3 complient bitstream"

---

### Post by sb73542 on 2005-10-02
Well, a "bitstream" would be generated by reading or writing an MP3 file, correct?  It's a well done patent, unfortunately.

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=sb73542]
Does this apply if I'm using LAME or some other OSS encoder that hasn't payed anyone any royalties?  And what about a non-profit (and low income too) organization?  The MP3's are absolutely not being sold, but it's not exactly a private user...[/QUOTE]

I think you found the clause you needed. As long as the org does not sell them, that says that they can be made.

Use Lame with pride. You just found the loophole you needed.

---

### Post by Kyral on 2005-10-02
[quote=sb73542]Well, a "bitstream" would be generated by reading or writing an MP3 file, correct? It's a well done patent, unfortunately.[/quote]

I think the bitstream is the MP3 itself. So things like codecs would only read it...

---

### Post by sb73542 on 2005-10-02
:-)   ;-)

But I'd still be happy to give them their stinking $0.75 if it gave me more rights.

I assume this means that I am also allowed to listen to MP3's with any player I might choose, as long as I am not generating profit by listening to them?

Thanks for all your help!

---

### Post by Kyral on 2005-10-02
[quote=sb73542]:-)   ;-)

But I'd still be happy to give them their stinking $0.75 if it gave me more rights.

I assume this means that I am also allowed to listen to MP3's with any player I might choose, as long as I am not generating profit by listening to them?

Thanks for all your help![/quote]

Holy hell! He found the loophole that might let Ubuntu destribute MP3 codecs outta the box! SCORE!

---

### Post by bjweeks on 2005-10-02
I think it is .75 cents for a licence of the distribution of 1 mp3 enabled player, not the use of it.

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=Kyral]Holy hell! He found the loophole that might let Ubuntu destribute MP3 codecs outta the box! SCORE![/QUOTE]

Not quite. The company that develops Ubuntu is not a non-profit. So the developers would still be in legal danger.

But for this one use, a hole has been found. Thats using the old noggin.

---

### Post by sb73542 on 2005-10-02
I e-mailed mp3licensing.com with a near copy of my original post.  I'll copy it here in the event that they ever deign to reply to me.

---

### Post by bjweeks on 2005-10-02
So if I understand this ubuntu cant distribute lame with it, but I can install it legally correct?

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=bjweeks]So if I understand this ubuntu cant distribute lame with it, but I can install it legally correct?[/QUOTE]


I think thats the jist of it.

---

### Post by joelito on 2005-10-02
Actually, I think that as a foundation it would be legal to include lame, but I'm no lawyer or anything like that so I'm not entirely sure about this

---

### Post by sb73542 on 2005-10-02
If they wanted to, Ubuntu might be able to create a new non-profit organization and utilize it as the distribution engine for questionable software.

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=sb73542]If they wanted to, Ubuntu might be able to create a new non-profit organization and utilize it as the distribution engine for questionable software.[/QUOTE]

Well....Ubuntu is managed by a non profit  foundation but its developers work for a for profit company so....

---

### Post by joelito on 2005-10-02
Yes, ubuntu's core developers are canonical employees but many are not (Including the MOTU guys AFAIK) but I don't think that rule's about about the coders employer but the organization that runs the product

And Besides, some of Mark's $ 10mil donation and other aditional donations could be used to buy an mp3 license (if needed). If not then push a multiplataform ogg multimedia app to windows user (VLC is good for geeks but doesn't look right for average windows users)

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=joelito]
And Besides, some of Mark's $ 10mil donation and other aditional donations could be used to buy an mp3 license (if needed). If not then push a multiplataform ogg multimedia app to windows user (VLC is good for geeks but doesn't look right for average windows users)[/QUOTE]

I would rather all the money possible be spent on development. Mark recently bought Impilinux to deal with the codec problems:

[http://www.ubuntuforums.org/showthread.php?t=70349&highlight=impi](http://www.ubuntuforums.org/showthread.php?t=70349&highlight=impi)

---

### Post by mstlyevil on 2005-10-02
[QUOTE=sb73542]Thanks for your fast reply!

Hmmm.  I almost positive that Realplayer doesn't encode anything.  It only plays.

I guess I could just use Windows.  Anyone know if it's legal with a default Windows install?  Thanks![/QUOTE]


  If you use Win Media Player it is legal. Microsoft already charged you the fee when you bought windows.

---

### Post by blastus on 2005-10-02
[QUOTE=mstlyevil]If you use Win Media Player it is legal. Microsoft already charged you the fee when you bought windows.[/QUOTE]

A big fee I might add.

---

### Post by occy8 on 2005-10-03
There is some free stuff here
[http://www.all4mp3.com/tools/sw_fhg_cl.html](http://www.all4mp3.com/tools/sw_fhg_cl.html)
The use of this software is only allowed for personal and non-commercial purposes  
So you have to check weather non-profit means non-commercial, I think you asked them already in your mail.
I'm really interested in their answer.

---

### Post by bennyelee on 2005-10-03
[QUOTE=occy8]There is some free stuff here
[http://www.all4mp3.com/tools/sw_fhg_cl.html](http://www.all4mp3.com/tools/sw_fhg_cl.html)
[/QUOTE]
This website (all4mp3.com) also has some source code examples on how to use the acm filter driver that is installed with wmp10 to encode mp3 files. So, if you are building a windows application, you could legally use this to encode mp3 files (however the user would be required to have wmp10 installed (which I believe is winXP only)). [http://www.all4mp3.com/dev/](http://www.all4mp3.com/dev/)

---

### Post by sb73542 on 2005-10-03
I'm communicating back and forth with the company.  It is quite difficult to explain the exact situation to them as it applies to legal issues.  So the discussion is ongoing yet.

It sounds as though the distribution of CONTENT is what is specifically covered by that section I quoted from their site.  You can distribute MP3 files if you are non-profit and make <100k of revenue in doing so.  

The question in my mind now is: "Where is the content supposed to come from, and how can we listen to it?"  They did specifically mention to me  [http://www.all4mp3.com/tools/sw_fhg_cl.html](http://www.all4mp3.com/tools/sw_fhg_cl.html) , already mentioned here, but it's very limited software.  I'm not sure of the status of 3rd party software such as LAME, who freely develops and distributes an encoder/decoder.  We'll see.

---

### Post by sb73542 on 2005-10-04
Here it is.  
> Hello,
Yes, you are legally free to distribute mp3 files (although you may of
course need permission from the original content creators, such as
artists, studios, etc) up to and until you pass the $100,000 in annual
gross revenue threshold from mp3 distribution (not net revenues). 
As far as using various mp3 encoders/decoders, there are numerous mp3
applications available which are both free and licensed, such as WMP,
Real, MusicMatch, WinAmp, Yahoo, etc. These are all legal applications,
as they are already licensed. 
If you have a specific application for which the licensing information
is not clear, I'd be happy to check if it is licensed by us. 
Mp3 of course is open for all end-user applications (that is, we don't
license end-users), however when you get into the area of
re-distributing code or content, we get into the legal licensing area. 
I hope this provides more clarification. Please don't hesitate to
contact me with any further questions. 
Best regards,
Big Wig
mp3 licensing
Thomson
16935 W. Bernardo Drive, Suite 100
San Diego, California 92127
[email]bigwig@email.net[/email]
[www.mp3licensing.com](www.mp3licensing.com)
Thomson (Euronext Paris: 18453; NYSE: TMS) provides end-to-end solutions
(technologies, equipment and services) to the entertainment industries.
To advance and enable the digital media transition, Thomson has four
principal divisions: Content and Networks, Consumer Products,
Components, and Licensing. The company distributes its products under
the Technicolor, Grass Valley, THOMSON and RCA brand names.
For more information: [www.thomson.net](www.thomson.net)
CONFIDENTIALITY NOTICE: This e-mail contains information that is
privileged, confidential, and subject to legal restrictions and
penalties regarding its unauthorized disclosure or other use. You are
prohibited from copying, distributing, or otherwise using this
information if you are not the intended recipient. If you have received
this e-mail in error, please notify us immediately by return e-mail and
delete this email and all attachments from your system. Thank you.
-----Original Message-----
From:   [mailto: [email]fake@email.com[/email]] 
Sent: Monday, October 03, 2005 6:34 PM
To: Wig Big
Subject: Re: [ ] Legal MP3 Encoding in USA with Linux?
Hello again,
Thanks again for your help.
Yes, I would like to distribute MP3 content (files), not 
encoders/decoders. It sounds as though I am legally clear to distribute 
MP3 content, since the organization realizes $0 profit from distributing
said content- the files are given to the end users for free. Is this 
correct?
If so, the final question relates to the specific software I use to 
create the MP3 file. As I have mentioned, there exist on the Internet 
numerous freely distributed MP3 encoders/decoders. The individuals who 
design and distribute these encoders are in no way related to my 
organization. Nor do these individuals profit from the software they 
write. It is freely developed and freely distributed to any who find it 
useful. Am I in violation of your patents or EUA if I download, install,
and use such free MP3 encoders/decoders to create my MP3 content?
Thanks for your consideration.
Wig Big wrote:
Hello,
Thank you for your clarifications.
The statement you located on our website:
[[http://www.mp3licensing.com/help/#5](http://www.mp3licensing.com/help/#5)
However, no license is needed for private, non-commercial activities
(e.g., home-entertainment, receiving broadcasts and creating a
personal
music library), not generating revenue or other consideration of any
kind or for entities with associated annual gross revenue less than
US$
100 000.00.] refers to content distribution. If, in your application 
you are only distributing mp3 files, then this statement holds true.
This statement does not refer to redistributing encoders or decoders 
however. From your explanation, it seems you are referring to 
distribution of mp3 content. Is this correct? If so, then the answer 
you quoted from our website to Question #5: Do I need a license to 
distribute mp3, mp3PRO or mp3surround encoded */content/*? - is 
correct. Yes, you need a license for non-private distribution (whether
for-profit or non-profit), but only if your organization realizes at 
least $100,000 in mp3-related revenues or income annually.
Different licensing terms apply to the distribution of mp3 encoders 
and decoders, versus the distribution of mp3*/ content./*
*/ /*
I hope this has helped to clarify the issue. Please do not hesitate to
contact me if questions remain.
Best regards,
Big Wig
mp3 licensing
Thomson
16935 W. Bernardo Drive, Suite 100
San Diego, California 92127
[email]bigwig@email.net[/email]
[www.mp3licensing.com](www.mp3licensing.com)
Thomson (Euronext Paris: 18453; NYSE: TMS) provides end-to-end 
solutions (technologies, equipment and services) to the entertainment 
industries. To advance and enable the digital media transition, 
Thomson ance and enable the digital media transition, Thomson has four
principal divisions: Content and Networks, Consumer Products, 
Components, and Licensing. The company distributes its products under 
the Technicolor, Grass Valley, THOMSON and RCA brand names.
For more information: [www.thomson.net](www.thomson.net)
CONFIDENTIALITY NOTICE: This e-mail contains information that is 
privileged, confidential, and subject to legal restrictions and 
penalties regarding its unauthorized disclosure or other use. You are 
prohibited from copying, distributing, or otherwise using this 
information if you are not the intended recipient. If you have 
received this e-mail in error, please notify us immediately by return 
e-mail and delete this email and all attachments from your system. 
Thank you.
-----Original Message-----
From:   [mailto: [email]fake@email.com[/email]]
Sent: Monday, October 03, 2005 2:02 PM
To: Wig Big
Subject: Re: Legal MP3 Encoding in USA with Linux?
Hello,
Thanks for your reply. I have a few remaining questions.
First of all, I need to clarify that I am *not* developing or
distributing any software of any sort. I am personally directing the
department of the non-profit organization that requires the use of
MP3's. I merely wish to encode and decode MP3 files, utilizing one of
the plethora of "Open Source Software" programs that are already
available for Linux, as these suit my needs better than the tools
found
at [http://www.all4mp3.com/tools/sw_fhg_cl.html](http://www.all4mp3.com/tools/sw_fhg_cl.html) . Is this legal?
I am still confused as to the legal status of MP3 codecs for
non-profit
use on the Linux platform. For example, the following paragraph would
seem to indicate that I am free to use any program that reads or
writes
MP3's, as long as I am not profiting from it:
----------------
[http://www.mp3licensing.com/help/#5](http://www.mp3licensing.com/help/#5)
However, no license is needed for private, non-commercial activities
(e.g., home-entertainment, receiving broadcasts and creating a
personal
music library), not generating revenue or other consideration of any
kind or for entities with associated annual gross revenue less than
US$
100 000.00.
-----------------
Do I understand this correctly?
Thanks very much for your help.
Wig Big wrote:
Hello,
Thank you for contacting mp3 licensing.
We are happy to provide you with mp3 licensing information; our
licenses are open to any and all who wish to use the mp3 codec in
their applications, regardless of size.
To answer your questions below, you have several legal (and
cost-free)
options available to you. And of course, you may also take a direct
license if you determine that this route will be the way to go in
the
end analysis.
For one, while you may not (without a license) redistribute mp3
commandline tools yourself, you may point your clients to our free
commandline tools found at
[http://www.all4mp3.com/tools/sw_fhg_cl.html](http://www.all4mp3.com/tools/sw_fhg_cl.html)
Alternatively, you may write software using our tools for Windows
Media Player 10. You may use the free ACM example source code to
include encode and decode support in your application. And to answer
your question here: [Is it genuinely legal to encode MP3 using
Windows
out of the box?] - Yes, it is legal.
Our licensing terms for software, which can also be found here:
[http://www.mp3licensing.com/royalty/](http://www.mp3licensing.com/royalty/)
I've also included them here, if you decide that licensing the mp3
code is preferable to the options mentioned above:
The mp3 license terms for Thomson and FhG patents and software are:
For patents only (if you use your own or a third party codec):
$0.75 per decoder; or
$2.50 per codec (encode+decode).
Royalties are reported and paid on a calendar quarter basis.
There is an annual minimum royalty (AMR) of $15,000.00 due every
Jan.
1, against which the above running royalties are credited during the
same calendar year.
If this is too large a sum, we can reduce the AMR to $5,000.00, with
double the per unit royalties.
You may offer a limited free trial for codecs, which limit the
encoding (i) after a maximum of 20 files, or (ii) after a maximum of
30 days, with the intent of promoting full licensed codec versions.
For Patents + Fraunhofer software, the terms are the same, except
the
codec rate which is $5/unit for the $15k annual minimum, and
$10/unit
for the $5k annual minimum
To draft a license, we need:
- Official company name, headquarter address, and
country/state/province of incorporation;
- Contact person, address, phone, fax, and email, responsible for
this
agreement;
- Effective date.
t;
- Your choice of Annual Minimum ($15k or $5k)
Please let me know how you would like to proceed, and if you have
any
other questions (or if I've misunderstood your request) - please let
me know and we can go from there.
Thanks and best regards,
Big Wig
mp3 licensing
Thomson
16935 W. Bernardo Drive, Suite 100
San Diego, California 92127
[email]bigwig@email.net[/email]
[www.mp3licensing.com](www.mp3licensing.com)
Thomson (Euronext Paris: 18453; NYSE: TMS) provides end-to-end
solutions (technologies, equipment and services) to the
entertainment
industries. To advance and enable the digital media transition,
Thomson has four principal divisions: Content and Networks, Consumer
Products, Components, and Licensing. The company distributes its
products under the Technicolor, Grass Valley, THOMSON and RCA brand 
names.
For more information: [www.thomson.net](www.thomson.net)
CONFIDENTIALITY NOTICE: This e-mail contains information that is
privileged, confidential, and subject to legal restrictions and
penalties regarding its unauthorized disclosure or other use. You
are
prohibited from copying, distributing, or otherwise using this
information if you are not the intended recipient. If you have
received this e-mail in error, please notify us immediately by
return
e-mail and delete this email and all attachments from your system.
Thank you.
-----Original Message-----
From:   [mailto: [email]fake@email.com[/email]]
Sent: Sunday, October 02, 2005 4:45 PM
To: *SAND MP3 Info
Subject: Legal MP3 Encoding in USA with Linux?
Hello,
I am trying to set up a digital recording solution for a USA
non-profit
organization. I would like to use Linux because Windows costs too
much.
But I need to be able to encode some of the organization's
*original*
content to MP3 audio, so that it will work with people's MP3
players.
It's imperative that I use software that is 100% free of legal
issues in
the USA. I can't use anything shady or for which there exists even
the
possibility of legal trouble in the event of a government audit,
etc.
Would it be possible for me to use one of the many open source Linux
programs of my choice for MP3 encoding after paying MP3licensing
your
$0.75? Or do you only license to big companies in volume?
Is it genuinely legal to encode MP3 using Windows out of the box?
Please try to answer all of the above questions at your earliest
convenience.
Thanks for your help!


---

