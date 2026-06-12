---
title: "Kindle for PC /Wine"
date: 2009-11-14
forum: Wine
---

### Post by nealaustin on 2009-11-14
I tried to install Kindle for PC with wine but all of the screens from Installation to splash to function have no text. Has anyone gotten Kindle for PC to work?

Neal

---

### Post by afrodeity on 2009-11-17
> **nealaustin said:**
> I tried to install Kindle for PC with wine but all of the screens from Installation to splash to function have no text. Has anyone gotten Kindle for PC to work?

Neal

Me too. I even tried copying a Windows XP system32 folder over to WINE as recommended in one posting but no success. Wish it worked. it might be something to do with the way it connects to the internet? Seems to me, the text only comes up if it sees a connection.

---

### Post by afrodeity on 2009-11-17
Okay, this works - set the Windows version to Windows98 in Wineconfig :)

[http://lifehacker.com/5406505/run-kindle-for-pc-in-linux-with-wine](http://lifehacker.com/5406505/run-kindle-for-pc-in-linux-with-wine)

---

### Post by stecz on 2009-11-18
even when I have it set for win98, I still get an all white screen.  I haven't copied the win32 folder over yet...

Any other ideas?

---

### Post by nealaustin on 2009-11-18
I just tried the fix of setting wine to Win 98. Wow what an easy fix. Everything works! Thanks

---

### Post by afrodeity on 2009-12-02
I should probably add you can do this individually for applications in winecfg. Just add the application to application settings. Then you can have Win98 and XP.

---

### Post by Leppie on 2009-12-02
Where did you get the Kindle for PC app?

---

### Post by afrodeity on 2009-12-02
Amazon.com or google.

---

### Post by williamshome1 on 2009-12-22
I installed wine 1.2 today from Ubuntu 9.10
I then installed Kindle for PC and changed the winecfg to Windows 98 as instructed above.

When I try to start the application I see an application icon in the bottom panel of the screen indicating that its starting. But nothing ever shows in the content area.

---

### Post by afrodeity on 2009-12-25
I'm running Wine 1.1.35 so not sure if its a problem with your Wine version. Try adding kindle in **application settings** under winecfg and setting the windows version there.

---

### Post by williamshome1 on 2009-12-25
I set the Kindle application in the wine config and changed the setting to Windows 98. 

When I run the application from the command line I get the following output:

[B]mmap() failed: Cannot allocate memory
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:msimtf:DllCanUnloadNow ()[/B]

I saw some other traffic on this related to a game but not for the Amazon Reader. I suspect it has something to do with the Nvidia card/driver.

---

### Post by afrodeity on 2009-12-26
Second line looks like something to do with the sound setting in Wine. Try changing the sound option in winecfg.

There are quite a few bug reports related to the fixme

> Hi, when trying to help with recent bug 20616, i found out, that there is
recent regression. So because it does not happen in wine-1.1.32 and wine-1.1.33
is still not released, i left version as unspecified. Please correct if
wrong...


Another thing you could try to do is install:
 .net 2.0.

```
winetricks dotnet20
```

Not sure it it will help, but best to eliminate the possibility.

Otherwise you will either have to file a bug report with WINEHQ or downgrade your version of WINE I'm afraid. Sorry couldn't be of more assistance.

---

### Post by ibgeorgeb on 2009-12-26
I'm experiencing a similar problem. I see the Kindle for PC icon on my desktop but it will not launch Kindle4PC. I've tried the configure to 98 procedures. When I tried to configure and test my sound card, I hear a "click" -- the same sound that *espeak* makes. I hope that this issue can be resolved. Thank you in advance for any workable solution/s. gB

---

### Post by pietbarber on 2009-12-27
Hello gang. 
I have exactly the same issue. 
Here is a run down of what I have. 
I have an Acer Aspire One laptop running Ubuntu Netbook Remix, quite freshly built yesterday with all updates. 

I had this problem with the default wine install. 

I had this problem with the beta version of wine 
[FONT=Courier New]ii  wine1.2                   1.1.35-0ubuntu1           Microsoft Windows Compatibility Layer (Binary Emulator and Library[/FONT]

I have installed the winetricks dotnet20
Nothing I do gets the Kindle application to work. :(

```
piet@Sunny:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe 
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:msimtf:DllCanUnloadNow ()
piet@Sunny:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ 


```

---

### Post by afrodeity on 2009-12-27
It could be your graphics card, try:
```

winetricks d3dx9

```

---

### Post by afrodeity on 2009-12-27
It could be your graphics card, try:
```

winetricks d3dx9

```

---

### Post by ms602 on 2009-12-28
I'd bet that Amazon changed something, that the version up for download now is different than what was previously available.  I went to download the Kindle for PC app and install it on all my Ubuntu computers, and none of them work.  All Ubuntu PC's include a Sony Vaio notebook (Intelx64), an HP notebook (AMDx64), and an Acer Aspire One netbook (Intelx86).  I've tried to find a copy of the November 10th beta of Kindle for PC, but have not found a downloadable install any place except directly from Amazon.  If anyone has a copy of a prior version of Kindle for PC, known to work, please do post.

---

### Post by marco_craveiro on 2009-12-28
Hi,

a bit of a me-too post. was following instructions from [lifehacker]("http://lifehacker.com/5406505/run-kindle-for-pc-in-linux-with-wine") and the kindle for pc from [amazon]("http://d1xhj100piaj9u.cloudfront.net/25709/KindleForPC-installer.exe") but nothing happens when I run it from wine. Terminal says:
> 
[marco@perlis Kindle For PC]$ wine KindleForPC.exe 
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"


Really looking forward to buying ebooks. Any help would be greatly appreciated.

Thanks

Marco

---

### Post by chipr on 2009-12-28
I'm also having problems running the "Kindle for PC" software.  Here is the error I'm getting:

```
$ wine KindleForPC.exe
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xdfa1bc)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
fixme:crypt:CertGetNameStringW unimplemented for type 2
fixme:msimtf:DllCanUnloadNow ()
```

This is on Ubuntu 9.10 x86_64 with Wine 1.0.1-0ubuntu8.
I set Windows version to "Windows 98".
I've also installed winetricks dotnet20 and d3dx9

Any suggestions on what I might try?

---

### Post by ms602 on 2009-12-29
Yup, that's the problem.  Amazon changed something that broke it for Ubuntu.  You'd think that Amazon would be a bit more appreciative towards Linux, given that the Kindle runs it! We should all demand that Amazon provide a Linux version of 'Kindle for PC'!!! But anyhow... here's where you can download the original 'Kindle for PC' beta file.  I would highly suggest ya'll grab it while the grabbing is good, before Amazon notices and requests a cease and desist.  Whatever they have up on Amazon.com right now won't work, though it would be wonderful if someone would find a workaround for that, because I wouldn't be surprised if Amazon cuts off access to prior beta installs at some point and demands an upgrade.

[http://www.tucows.com/download.html?software_id=613764&t=2](http://www.tucows.com/download.html?software_id=613764&t=2)

Captain's Log, Supplemental:  Amazon is really starting to piss me off.  They've clearly made changes that break 'Kindle for PC' for Wine.  I don't know if this is intentional or unintentional, but I really think that us users need to demand a native Linux edition.  The original 11/10 beta file will install and get to login, but will fail to authenticate with Amazon's servers (even with the Windows 98 wine setting).  On the Kindle device list, it shows an authorization for EVERY attempt to login, yet the software will not recognize as authenticated, and thus content cannot be accessed.  Whatever version of the beta that Amazon has up as of yesterday (12/28) will not load at all.  I get the same errors listed by previous commenters in this thread.

---

### Post by chipr on 2009-12-29
> **ms602 said:**
> Yup, that's the problem.  Amazon changed something that broke it for Ubuntu. ... But anyhow... here's where you can download the original 'Kindle for PC' beta file.

Thanks, this version installed and ran fine.

---

### Post by pietbarber on 2009-12-29
> **afrodeity said:**
> It could be your graphics card, try:
```

winetricks d3dx9

```

Did that this morning.  Still no soup: :( 

```
piet@Sunny:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe 
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:msimtf:DllCanUnloadNow ()
piet@Sunny:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ 

```

---

### Post by pietbarber on 2009-12-29
> **ms602 said:**
> Yup, that's the problem.  Amazon changed something that broke it for Ubuntu.  You'd think that Amazon would be a bit more appreciative towards Linux, given that the Kindle runs it! 

[http://www.tucows.com/download.html?software_id=613764&t=2](http://www.tucows.com/download.html?software_id=613764&t=2)


I have downloaded this version, and it works for me.  Thanks guys.

---

### Post by geneven on 2009-12-29
Thanks for figuring out that the problem is the version of Kindle for PC! I am the "User Gene" who reported how well this worked to Lifehacker! I have spent many hours happily running Kindle for PC and to have it suddely taken away was a drag!

---

### Post by pietbarber on 2009-12-30
So I guess the next question is, do we send this as a bug report to the Wine developers or do we send it to Amazon, or both? 

This beta isn't going to last forever.

---

### Post by SethK on 2009-12-30
I was also able to install the old Beta and have is successfully run with Wine. I have also used VirtualBox to run a copy of Windows XP and of course Kindle PC works with that. BUT that seems a little cumbersome to read eBooks and not a viable solution for netbook users. I am anxiously awaiting to see if Kindle offers Linux support.

---

### Post by Hawkken on 2010-01-02
I have been pulling my hair out for a week trying to figger out what the heck was going on here.  I moved from remix to 9.1 full on my laptop.  I was just have to many problems with remix.

I was so upset when I could not get the Kindle app running again, that I was almost ready to reinstall the remix just for my books...:confused:

But the old betta has me up a reading again.  Thanks so much for this find.
I sure hope Amazon sees this as a bo-bo and fixes it soon.

---

### Post by imakeart on 2010-01-02
Thank you!!

I've been fiddling with Kindle for PC for a couple days now with no luck. Decided to come back to this thread and see if anyone else had any luck and saw the news about the beta version.

I do hope Amazon does a Kindle for Linux!

---

### Post by chipr on 2010-01-03
If you'd like to see this fixed, file a bug report with Amazon.

To do so, go to the Kindle Support page: [http://www.amazon.com/gp/help/customer/display.html/ref=sv_kinc_8?ie=UTF8&nodeId=200127470](http://www.amazon.com/gp/help/customer/display.html/ref=sv_kinc_8?ie=UTF8&nodeId=200127470)

Click the "Contact US" button in the right sidebar.

Then enter your problem report.  Here is what I sent:

[INDENT]Issue: Computer or Mobile Phone Reader Issue
Kindle Version: Kindle for PC

Previous versions of the "Kindle for PC" software worked under WINE, the Windows Emulator for Linux.  The current version does not.  The application installs correctly, but when you try to launch the program it fails to run.

Could you please forward a request to the development team to test releases under WINE?  Thanks.[/INDENT]

**UPDATE:** The initial response from Amazon response was unhelpful -- it suggested I reinstal Kindle for PC.

I clicked the "No, this doesn't answer my question" link in the response email. A couple hours later, I got a better response that said:

[INDENT]I've reviewed our previous correspondence with you, and I'm very sorry about the misunderstanding you received.

Strong customer feedback like yours helps us continue to improve the service we provide, and we're glad you took time to write to us about working on "Kindle for PC" under WINE, the Windows Emulator for Linux.

I'll send your comments to the Kindle team.[/INDENT]

So, please do consider submitting feedback -- and be sure to escalate if the initial response isn't helpful.

---

### Post by ibgeorgeb on 2010-01-03
Great! Amazon should have my comments now. Thank you for the heads up. gB

---

### Post by ms602 on 2010-01-04
I think we need to take more drastic measures...  Not that Linux gurus are easy to politically organize, but it's worth a shot.  I've created a Facebook fanpage for the cause.  This may be difficult, considering that it's incredibly hard to even raise people's conscious..  But comon people, let's unite!  Join this group!  And invite people, especially Linux users.. They know the pain of having to play with Windows applications to get working..

[http://www.facebook.com/pages/Kindle-for-Linux/259304580762](http://www.facebook.com/pages/Kindle-for-Linux/259304580762)

Join now to demand that Amazon support Linux!  Kindle for Linux!  Not just Kindle for Windows!

---

### Post by Hallvor on 2010-01-04
So you basically ask them for help to run their DRM infested files using a closed source third party application? 

The solution is here:
[http://news.cnet.com/8301-17938_105-10421296-1.html](http://news.cnet.com/8301-17938_105-10421296-1.html)

I don`t know how it is in other countries, but in Norway we have a legal right to circumvent/destroy DRM to use purchased digital files on any relevant media equipment.

If you buy a PDF with DRM you have the right to remove the DRM to view it on your computer using Evince or whatever your PDF viewer is - at least here.

---

### Post by Spiritof76 on 2010-01-04
Amazons DRM is devious and particularly nasty. They removed books from peoples Kindles after they had bought them. To give Amazon access to our computers seems to be a very bad Idea.

---

### Post by bdws1975 on 2010-01-07
I did this as well AND I notified them of the facebook page pleading for a linux version of the app.

I was very nice and respectful.  We'll see what happens.

thanks,
Brett

> **chipr said:**
> If you'd like to see this fixed, file a bug report with Amazon.

To do so, go to the Kindle Support page: [http://www.amazon.com/gp/help/customer/display.html/ref=sv_kinc_8?ie=UTF8&nodeId=200127470](http://www.amazon.com/gp/help/customer/display.html/ref=sv_kinc_8?ie=UTF8&nodeId=200127470)

Click the "Contact US" button in the right sidebar.

Then enter your problem report.  Here is what I sent:
[INDENT]Issue: Computer or Mobile Phone Reader Issue
Kindle Version: Kindle for PC

Previous versions of the "Kindle for PC" software worked under WINE, the Windows Emulator for Linux.  The current version does not.  The application installs correctly, but when you try to launch the program it fails to run.

Could you please forward a request to the development team to test releases under WINE?  Thanks.[/INDENT]**UPDATE:** The initial response from Amazon response was unhelpful -- it suggested I reinstal Kindle for PC.

I clicked the "No, this doesn't answer my question" link in the response email. A couple hours later, I got a better response that said:
[INDENT]I've reviewed our previous correspondence with you, and I'm very sorry about the misunderstanding you received.

Strong customer feedback like yours helps us continue to improve the service we provide, and we're glad you took time to write to us about working on "Kindle for PC" under WINE, the Windows Emulator for Linux.

I'll send your comments to the Kindle team.[/INDENT]So, please do consider submitting feedback -- and be sure to escalate if the initial response isn't helpful.

---

### Post by emt_1 on 2010-01-16
I have tried all the above steps without success (9.10)and only want to say that it does work on Linux as I have it working on Debian 5.0.So could be kernel version?,wine version?,ubuntu(wouldn't install on 9.04)?

---

### Post by emt_1 on 2010-01-16
update from previous post On Debian 5.0 Wine ver. 1.01,Kernel ver.2.6.26-2-amd64,kindle ver.1.0 beta works.

---

### Post by waspbr on 2010-01-19
I have tried on both karmic and lucid under the latest wine, both seem to be able to install the kindle for PC but they do not seem to be able to run it. 

That being aid I was able to successfully install the program a while back in my Desktop with an older installation file and it runs perfectly.

---

### Post by pietbarber on 2010-01-24
[http://bugs.winehq.org/show_bug.cgi?id=21485](http://bugs.winehq.org/show_bug.cgi?id=21485)

I've submitted this as a bug into the WINE Bugzilla repository.

---

### Post by pietbarber on 2010-01-25
The wine guys asked me to try a patch; I won't be able to check it out for a few days yet, but the rest of you might find it useful:

If anybody wants to try giving it a spin, the URL for the patch is in the bugzilla ticket. 

Wine bug URL: 
[http://bugs.winehq.org/show_bug.cgi?id=21485](http://bugs.winehq.org/show_bug.cgi?id=21485)

Patch link: 
[http://bugs2.winehq.org/attachment.cgi?id=24914](http://bugs2.winehq.org/attachment.cgi?id=24914)

---

### Post by apswartz on 2010-02-01
> **ms602 said:**
> Yup, that's the problem.  Amazon changed something that broke it for Ubuntu.  You'd think that Amazon would be a bit more appreciative towards Linux, given that the Kindle runs it! We should all demand that Amazon provide a Linux version of 'Kindle for PC'!!! 

Amen! What's up with not supporting Linux on the desktop when it runs the device?

---

### Post by panthermartin on 2010-03-16
Many of the download sites have now replaced the beta file with the newer non-beta that does not work in Wine, even some that say its the beta (like Tucows).  However the following site still has the beta, grab it while you can.  Watch the file size, if it's 6.0 MB, then its likely the new one, the beta is 5.2 MB.
[http://www.softpedia.com/progDownload/Kindle-for-PC-Download-143957.html](http://www.softpedia.com/progDownload/Kindle-for-PC-Download-143957.html)

---

### Post by raynman on 2010-03-23
> **panthermartin said:**
> Many of the download sites have now replaced the beta file with the newer non-beta that does not work in Wine, even some that say its the beta (like Tucows).  However the following site still has the beta, grab it while you can.  Watch the file size, if it's 6.0 MB, then its likely the new one, the beta is 5.2 MB.
[http://www.softpedia.com/progDownload/Kindle-for-PC-Download-143957.html](http://www.softpedia.com/progDownload/Kindle-for-PC-Download-143957.html)


This post was a great help. I use the link from this site (5.2 MB size file) and kindle work flawlesly on my system in Windows 98 mode. This is after the new version did not work at all.

---

### Post by pabloikba on 2010-03-30
Thanks for all the work. I looked for the first time today to find out how to install Kindle for PC on Karmic. Using the beta version worked perfect for me on both desktop and laptop.

Pablo

---

### Post by binaryflow on 2010-04-16
Has anyone tried running the patch referenced in the wine bug report?  I'm curious to see if the new version works with the patch...

---

### Post by ourladyoflinux on 2010-05-08
> **raynman said:**
> This post was a great help. I use the link from this site (5.2 MB size file) and kindle work flawlesly on my system in Windows 98 mode. This is after the new version did not work at all.

Thanks so much, panther!  It finally worked for me.  Also, a silly mistake I made was not deleting the 'fake' beta file before I ran the new one.

---

### Post by manoynmonic on 2010-05-09
The 5.2mb beta works perfect.  Thanks for posting.  With it in win98 mode running in wine, KindleForPC still looks like crap though unless you enable anti-aliasing.

FWIW, this guy has a nice tutorial with a link to a script that sets up font anti-aliasing in wine.([http://www.wine-reviews.net/wine-reviews/tips-n-tricks/how-to-enable-font-anti-aliasing-in-wine.html](http://www.wine-reviews.net/wine-reviews/tips-n-tricks/how-to-enable-font-anti-aliasing-in-wine.html))

-mn

---

### Post by mister_p_1998 on 2010-05-25
They've changed it again! its 6.2mb!
any other links?
Steve

---

### Post by manoynmonic on 2010-05-25
Here is a link to my copy of the old beta.

[http://rapidshare.com/files/391386558/KindleForPC-installer.tar.html](http://rapidshare.com/files/391386558/KindleForPC-installer.tar.html)

MD5: 27F00FC9BD1498815AC24192283EF0A0

---

### Post by clegends on 2010-05-25
Awesome. Thanks heaps. Old version runs fine.

---

### Post by mister_p_1998 on 2010-05-26
Thanks, works great...

---

### Post by ajkessel on 2010-05-31
Does anyone have a link to the old 5.2MB version? None of the ones from this forum seem to work anymore. Alternatively, any progress on a workaround or fix?

---

### Post by gauravm on 2010-06-06
[http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however.

---

### Post by mediamind on 2010-06-09
> [http://www.blogsdna.com/5575/read-ki...or-pc-beta.htm](http://www.blogsdna.com/5575/read-ki...or-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however. 

I can confirm this version worked with Lucid (64-bit) running Wine 1.2-rc2.

---

### Post by 1111000110 on 2010-06-21
> **gauravm said:**
> [http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however.

Confirmed on Karmic w/ Wine 1.0.1.

---

### Post by Franko30 on 2010-06-26
> **gauravm said:**
> [http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however.

Hi,

the obove link still gives the BETA version which works as explained when setting Win98 in wine for Kindle.

Ubuntu 10.04, current updates with wine 1.2 rc4

Cheers

Franko30

---

### Post by wgarider on 2010-06-29
Thanks everyone here for the advice - reading this thread led me to fix the issues I had.

---

### Post by jashuff on 2010-07-14
I wish I could say that this thread helped me.  I've tried every tip in this thread, every tip that I can find anywhere and I always get the same error:

fixme:system:SetProcessDPIAware stub!

And only that error.  The program never starts.

Does anyone know what this might be?

---

### Post by manoynmonic on 2010-07-24
Looks like the blogdna file is gone.  Here is the old beta again:

[http://www.mediafire.com/?l5c3ozmtvdebmrf](http://www.mediafire.com/?l5c3ozmtvdebmrf)

---

### Post by wjanowski on 2010-08-10
I don't see why you're all going through too much trouble.  If you want to really express your concern to Amazon, get Barnes & Noble's Nook application and buy your e-books from them.  The Nook app runs flawlessly under Wine 1.2.

---

### Post by bonzini on 2010-08-14
Here is another alternative, and it doesn't need Wine.

Chapters-Indigo, a large Canadian book chain, markets a reader called "Kobo".  They also have free Windows and Mac clients....

AND they have a Linux client too!!!

Which I have used for about three weeks now.  It's not perfectly bug-free, but it's a pretty great reading experience nonetheless.

I suggest anyone interest contact their customer care folks, who are very responsive.  I would post the link but I think it's better to ask them directly since we all want them to know we value the effort they've made to provide a Linux e-reader!

Email to support at kobo point zendesk point com and ask them about it!

---

### Post by mjumbewu on 2010-08-26
> **manoynmonic said:**
> Looks like the blogdna file is gone.  Here is the old beta again:

[http://www.mediafire.com/?l5c3ozmtvdebmrf](http://www.mediafire.com/?l5c3ozmtvdebmrf)

Thanks, that link worked for me!

---

### Post by the_flumps on 2010-08-26
Worked for me too, thanks gang!

---

### Post by akshunj on 2010-08-27
the BETA from the mediafire link works great for me also. Lucid on a netbook. Ahhhh.....

---

### Post by monomox3000 on 2010-08-28
another happy customer, here
K4PC beta + Lucid Lynx + Wine 1.2 = :D

---

### Post by jud1929 on 2010-09-02
> **gauravm said:**
> [http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however.


I  can  confirm that this link works with Karmic and Wine1.2,  with the application environment set to Win98 in Wine config.

Tip on using wine: after the download completes go to Wine > Browse C:/ drive and navigate to the downloaded file. Then click to install the program. 

Thanks to you all for your help.

---

### Post by VanHammersly on 2010-09-09
I can also confirm link above works on 10.10.

---

### Post by bdws1975 on 2010-09-11
rockin!!!!  works like a charm.

thanks a bunch.

---

### Post by cemilhilton on 2010-09-12
> **VanHammersly said:**
> I can also confirm link above works on 10.10.

I'm on 64bit 10.10 beta and while the program loads flawlessly, it does not sync any of my purchases. Sending of samples also failed. Any thoughts?

---

### Post by Jazzy_Jeff on 2010-09-12
I would also recommend that you all send an email to Amazon to make a Linux version of their Kindle app. The more demand they have for it the more chance they will make it. Just like the mp3 downloader they made for us. I know a lot of people contacted Hulu for a Linux desktop version and now we have it. Just keep bugging these companies.

---

### Post by solarbattery on 2010-09-14
Thanks for the forum input, everyone.   I have installed the beta and it works perfectly on my system. Regards, :popcorn:

---

### Post by woohhaa on 2010-09-14
> **gauravm said:**
> [http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm)

that seems to be the older version....i have yet to try to install it myself however.

This is exactly why I love Ubuntu and it's community. Thanks so much to everyone who took the time to figure this out and rehost or hunt down the old installer. Works like a charm.

---

### Post by scummchild on 2010-09-17
> **cemilhilton said:**
> I'm on 64bit 10.10 beta and while the program loads flawlessly, it does not sync any of my purchases. Sending of samples also failed. Any thoughts?

I'm getting a similar issue on 32bit 10.10 beta (Netbook).  I installed using the old beta file, setting to win 98, etc. and the app seems to open fine.  I'm also thinking I'm registered correctly because the window title shows "[My Name Here]'s Kindle for PC 5."  But when I select "Sync and Check for New Items" in the bottom corner it says "Finished" (i.e., no error)...but my Archive Items contains 0 items.

On my desktop (10.04 64 bit) I also installed to compare, but in this case it works.  The app finds the 50ish items I have and I can open them, etc.

I tried removing my ~/.wine folder and reinstalling just for good measure.  Alas!  No dice!

I notice that [http://nomo17k.wordpress.com/2010/06/11/installing-kindle-for-pc-on-debian-squeeze/](http://nomo17k.wordpress.com/2010/06/11/installing-kindle-for-pc-on-debian-squeeze/) grabs the lib32nss-mdns package.  Would the app be sensitive to me not having a /lib/lib32 directory?  cemilhilton, do you have that package?  

My next thought was to make some symbolic links to my libnss_mdns* files from a dummy /lib/lib32 directory, but it feels like a long shot and I'm getting sleepy :p

When I call the app from the command line, my output looks like the following:

```
~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe fixme:win:FlashWindowEx 0x32da78
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:win:FlashWindowEx 0x32db30
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 240000
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:win:FlashWindowEx 0x32baf0
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 240000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
```

Any thoughts would be greatly appreciated!  :D

---

### Post by jgbelacqua on 2010-09-17
I didn't have trouble on 64-bit 10.04 either, so it sounds almost like a 10.10-related thing.   You might try uninstalling wine (and the kindle beta) and going with the wine1.3 dev code -- but this is probably a long shot.

---

### Post by scummchild on 2010-09-18
> **jgbelacqua said:**
> I didn't have trouble on 64-bit 10.04 either, so it sounds almost like a 10.10-related thing.   You might try uninstalling wine (and the kindle beta) and going with the wine1.3 dev code -- but this is probably a long shot.

Thanks!  Good suggestion.  I did this, but with the same results:

```
wine KindleForPC-installer.exe 
fixme:win:FlashWindowEx 0x33df48
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:win:FlashWindowEx 0x33e000
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImmReleaseContext (0xc0022, 0x1635a0): stub
fixme:win:FlashWindowEx 0x33df24
fixme:win:FlashWindowEx 0x33e2f4
fixme:win:FlashWindowEx 0x33c8f0
fixme:win:FlashWindowEx 0x33a280
fixme:win:FlashWindowEx 0x336780
fixme:win:FlashWindowEx 0x33c140
fixme:win:FlashWindowEx 0x33a658
fixme:win:FlashWindowEx 0x33bfc0
garison@Gracie:~/Downloads$ fixme:win:FlashWindowEx 0x336780
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:win:FlashWindowEx 0x33a644
fixme:win:FlashWindowEx 0x33a3c0
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:win:FlashWindowEx 0x33c078
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 240000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1

 wine KindleForPC.exe 
fixme:win:FlashWindowEx 0x32da78
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:win:FlashWindowEx 0x32db30
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 30000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 240000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
```

I really don't know what I'm talking about, but I still wonder if it has something to do with mdns.  On my 10.04 desktop (64bit), when I look at the wine dependencies, it lists the lib32nss-mdns package.  But on the 10.10 netbook (32bit, running gnome not unity)...I don't see any mention of a mdns package.  Did something change in 10.10 regarding mDNS?  The netbook does have the libnss-mdns package, so I'm probably smoking something!

---

### Post by skiquel on 2010-09-19
> **scummchild said:**
> I'm getting a similar issue on 32bit 10.10 beta (Netbook).  I installed using the old beta file, setting to win 98, etc. and the app seems to open fine.  I'm also thinking I'm registered correctly because the window title shows "[My Name Here]'s Kindle for PC 5."  But when I select "Sync and Check for New Items" in the bottom corner it says "Finished" (i.e., no error)...but my Archive Items contains 0 items.

Ditto, Wine 1.3.3 dev here.

Implementation wasn't retreiving with wine 1.2 from server or the latest 1.3.

Curious - For those who have it working, what version of Wine and Ubuntu are you running? You can use ```
wine --version
``` and ```
cat /etc/lsb-release
``` to see.

---

### Post by scummchild on 2010-09-19
> **skiquel said:**
> 
Curious - For those who have it working, what version of Wine and Ubuntu are you running?

On my desktop where it is working I have...

wine 1.1.42
Ubuntu 10.04 (64bit)

---

### Post by skiquel on 2010-09-27
> **scummchild said:**
> On my desktop where it is working I have...

wine 1.1.42
Ubuntu 10.04 (64bit)

What seemed to make the difference for me was (a la first page) going into ```
winecfg
``` and running the environment in Windows 98 mode.

Can you give it a shot?

---

### Post by scummchild on 2010-09-28
> **skiquel said:**
> What seemed to make the difference for me was (a la first page) going into ```
winecfg
``` and running the environment in Windows 98 mode.

Can you give it a shot?

Thanks.  Yeah, that's how I installed it too, but no luck though.  I made sure the installer and the KindleforPC.exe were set to Windows 98 in the wine cofiguration app.  Again, the app opens and seems to find my registration because the computer name changes but it doesn't find any purchases.  Something different about 10.10 I guess!

---

### Post by psykatog on 2010-09-29
Not sure if the same solution has been posted here yet, so sorry if that's the case.  I just saw that the topic still looks like it's active.  

I made a post over on the kubuntu boards that's worked for me on kubuntu, UNR, xubuntu, and Mint (KDE & XFCE) just fine.  Good luck!  I'm working on finding simple instructions for removing drms next...

> 
This isn't a problem, just a success that I thought I'd share since finding answers via googling was a bit harder than most __-buntu inquiries.  Not sure where this should be posted, really.  The only relevant search on the board was [this thread]("http://kubuntuforums.net/forums/index.php?topic=3107955.0"), which didn't offer much.


Step 1 - install Wine (obvious)
```
sudo apt-get install Wine
```One (probably older) site suggested this command, but it didn't work in terminal for me : 
```
 sudo apt-get install wine lib32nss-mdns
```Step 2 - download winetricks 
```
wget http://www.kegel.com/wine/winetricks
```Step 3 - adjust "corefonts" - a lot of people seem to have the issue that they can't read the kindle app's text once it loads in wine.  This seems to pre-empt that issue.  If you DO have that issue, configure wine to "windows 98" and go to "add application" and find the amazon app (if you've downloaded it already, it's a later step in these instructions).  Also, you can just enter your amazon email, hit tab, and then your password.  
```
sh winetricks corefont
```Step 4 - Download the kindle app - you can do this from Amazon, but inputting this command into terminal yields the same result.
```
wget http://ap.smu.ca/~taro/software/KindleForPC-installer.exe
```Step 5 - Up and running!
```
wine KindleForPC-installer.exe
```Again, a common complaint I got from scanning google results is that some people can't read the program's default display.  Like I said though, just make sure you configure wine to windows 98 for use with this app.  Hopefully this works!  I'm on Kubuntu Lucid 10.04 and this worked great for me.  Before I had resorted to setting up an Android emulator and running the kindle for android app, but this is much more straightforward.

**EDIT - UPDATES**
Here's a useful program for converting files to kindle format without paying amazon's 10-cent conversion fee (also windowsware :( : 
 [http://download.cnet.com/8301-2007_4-10187502-12.html](http://download.cnet.com/8301-2007_4-10187502-12.html)


---

### Post by kibatme on 2010-10-01
Was unable to run any version of Kindle for PC under Wine 1.2.  Installed Wine 1.3.3 and it runs version 1.0 Beta 1 version of Kindle with no obvious problems even with Windows 7 set in the Application Settings.  Downloaded the current version of Kindle for PC but no joy -- Wine clocks for 10 seconds or so but nothing happens.  Reinstalled the beta version of Kindle and back working again.  Too bad -- could really make use of the new features in Kindle for PC.  :(

---

### Post by scummchild on 2010-10-03
> **scummchild said:**
> Thanks!  Good suggestion.  I did this, but with the same results


Yay!  I'm on the wine ppa and got an update yesterday that did something to fix the issue.  I can now open the app AND see my purchases.  So, the issue seeing purchases on ubuntu 10.10 seems to be resolved with wine 1.3.4.

---

### Post by thezood on 2010-10-04
> **scummchild said:**
> Yay!  I'm on the wine ppa and got an update yesterday that did something to fix the issue.  I can now open the app AND see my purchases.  So, the issue seeing purchases on ubuntu 10.10 seems to be resolved with wine 1.3.4.

*rejoicing*

Now, if the new version would work so that we could read in full screen, it would truly be cause for a celebratory dance!

---

### Post by itl932 on 2010-10-14
Have just succeeded in getting Kindle to work on an Asus EeePC 900 running Wine 1.3.4 and the beta Kindle from the link below.  Thanks for all the useful postings. :)

Originally Posted by **gauravm** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9422287#post9422287") 				
 				[http://www.blogsdna.com/5575/read-ki...or-pc-beta.htm]("http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm")

---

### Post by henrywm on 2010-10-18
Kindle for PC will not work for me. I installed it with WINE. Now when I click the icon it will say in the taskbar that it is loading and then quit.

---

### Post by pietbarber on 2010-10-21
the WINE developers say they have fixed this bug in wine version 1.1.35. :P
[http://bugs.winehq.org/show_bug.cgi?id=21485](http://bugs.winehq.org/show_bug.cgi?id=21485)

I'll be trying this out over the next few days, so maybe this link will help you to get your Kindle application to work on Ubuntu.

---

### Post by henrywm on 2010-10-21
I have Wine 1.2.1.

---

### Post by Nickynak on 2010-10-25
The link in post 83 works with Wine set to Windows 98, have tried it, downloaded several books ( many are free on Amazon). I am using the the latest Wine available from Debian Unstable but I imagine it will work on the beta posted in that post in Ubuntu. Thanks for the links!

---

### Post by henrywm on 2010-10-28
I tried it with Wine set to Win98. It did not work. Kindle for PC tries to load and then quits without an explanation.

---

### Post by gavinjb on 2010-11-08
I have wine 1.2.1 and have set the default windows version to win98 for kindleforpc.exe and I get the kindle loading in taskbar and then nothing, but if I try running it in console I get the following

```

gavin@Linux-Laptop:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe 
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:create_server class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {6e4fcb12-510a-4d40-9304-1da10ae9147c} could be created for context 0x17
gavin@Linux-Laptop:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ 

```

Any ideas?

Thanks,



Gavin,

---

### Post by Johnny Utah on 2010-11-11
These instructions worked for me on Ubuntu 10.10:

[http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html](http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html)

---

### Post by sunset on 2010-11-13
> **Johnny Utah said:**
> These instructions worked for me on Ubuntu 10.10:

[http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html](http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html)

Wow that works, and easy as pie!  Thanks!

---

### Post by zagabog on 2010-11-14
Thanks Johnny Utah, that worked for me too. Now I don't have to take both the Kindle and laptop.

---

### Post by wolferl on 2010-11-16
> **sunset said:**
> Wow that works, and easy as pie! Thanks!
 
Same here. It even installs a nice kindle-amazon icon for the app, and another icon for the kindle-file type. Another +1 for Ubuntu \\:D/

---

### Post by kshsj777 on 2010-11-21
> **gavinjb said:**
> I have wine 1.2.1 and have set the default windows version to win98 for kindleforpc.exe and I get the kindle loading in taskbar and then nothing, but if I try running it in console I get the following

```

gavin@Linux-Laptop:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ wine KindleForPC.exe 
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:create_server class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {6e4fcb12-510a-4d40-9304-1da10ae9147c} could be created for context 0x17
gavin@Linux-Laptop:~/.wine/drive_c/Program Files/Amazon/Kindle For PC$ 

```

Any ideas?

Thanks,



Gavin,

I get this exact same error.  The first time I did the installation, the program opened once but I clicked out of it without registering.  I tried uninstalling and reinstalling the program but I still get the same error.

---

### Post by ajackson on 2010-11-22
> **kshsj777 said:**
> I get this exact same error.  The first time I did the installation, the program opened once but I clicked out of it without registering.  I tried uninstalling and reinstalling the program but I still get the same error.

Have you installed Wine 1.3 like the advice says?

---

### Post by kshsj777 on 2010-11-22
> **ajackson said:**
> Have you installed Wine 1.3 like the advice says?

At first, I had 1.2 installed, but then I installed 1.3 and that's when I got the error in the terminal.

---

### Post by kshsj777 on 2010-11-24
Ok, I figured out the problem was that I didn't have the beta for the Kindle for PC which works perfectly.  The beta will be 5.2mb in size.  The current version is over 12mb which doesn't work. (At least not on my computer.)

---

### Post by ajackson on 2010-11-25
The link posted by JohnnyUtah shows you how to get the proper version of Kindle for PC working or at least it worked for me.

---

### Post by sebe on 2010-11-29
Thanks guys this method worked fine on my 32bit N150 Pixel Qi netbook.
After an auto update, am now running version 1.1.0(30136) which has full screen mode.

[http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html](http://jessejamesa.blogspot.com/2010/11/installing-amazon-kindle-for-pc-on.html)

---

### Post by erikvw on 2010-12-28
After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.

First...

```
[B]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3[/B]
```

Second...

Download Kindle for PC and right mouse click on the file to "open with wine windows program loader".

---

### Post by vevel on 2010-12-28
@ erikvw : Awesome; thanks!  
I have been running the ppa wine 1.3, so all I had to do was to grab the kindle for PC app from the amazon page.  Bingo, it works.... 
I'm running 32-bit 10.10 .

> **erikvw said:**
> After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.


---

### Post by dierdorf on 2010-12-29
> **kshsj777 said:**
> I get this exact same error.  The first time I did the installation, the program opened once but I clicked out of it without registering.  I tried uninstalling and reinstalling the program but I still get the same error.
I found out how to get rid of the "OLE" error which makes installation of the "real" Kindle reader fail.  This assumes Maverick 64-bit and Wine 1.3 are installed.  It's kind of drastic if you have a lot of Wine applications installed, but it works.

Step Zero:  download the latest from Amazon.  It should be 12,850,600 bytes.
Step One:  >sudo apt-get purge wine1.3
Step Two:  >sudo rm -r ~/.wine  (maybe back up the directory structure elsewhere first)
Step Three:  >sudo apt-get autoremove
At this point Maverick is a virgin with respect to Wine.
Step Four:  >sudo apt-get install wine1.3
Step Five:  >wine  				 				 					 						[Forgotten Your Pass]("http://ubuntuforums.org/login.php?do=lostpw")KindleForPC-installer.exe  (the latest one you just downloaded)
Enjoy!

If somebody feels like figuring out exactly which part of the Wine structure causes the problem, this could probably be made less drastic.

---

### Post by jtuchscherer on 2010-12-30
Oh, I hope someone figures out another solution to the OLE problem. Purging wine would be pretty unfortunate for me. I have quite a few wine apps installed.

---

### Post by phelcq on 2010-12-31
I've managed to install Kindle for PC (latest version) on Wine 1.3.10 and it opens nicely, but I've got problems registering.
After filling the fields with my Amazon account details and waiting for a moment I get the info:

[INDENT]"Unable to connect at this time. Please try again later"[/INDENT]

Anyone had something similar happen? Any advice?

The other thing is: in Help menu there'a a 'Check for problems' option. It gives the output:
[INDENT]V  Network connection[/INDENT]
[INDENT]V  Hard Drive Free Space[/INDENT]
[INDENT]X  Secure Storage  (HELP) [/INDENT]

The Help section that opens directs to non-existing locations in the home folder. Any ideas? :)

---

### Post by Jazzy_Jeff on 2010-12-31
> **phelcq said:**
> I've managed to install Kindle for PC (latest version) on Wine 1.3.10 and it opens nicely, but I've got problems registering.
After filling the fields with my Amazon account details and waiting for a moment I get the info:

[INDENT]"Unable to connect at this time. Please try again later"[/INDENT]

Anyone had something similar happen? Any advice?

The other thing is: in Help menu there'a a 'Check for problems' option. It gives the output:
[INDENT]V  Network connection[/INDENT]
[INDENT]V  Hard Drive Free Space[/INDENT]
[INDENT]X  Secure Storage  (HELP) [/INDENT]

The Help section that opens directs to non-existing locations in the home folder. Any ideas? :)


Someone on the Kindle boards was complaining about this problem this morning using the Kindle for PC app running on Windows. Maybe their servers are down at this time. I would try again later and not mess with anything until you are sure the problem is on your end.

---

### Post by thespeth on 2010-12-31
I can't get wine to open Kindle at all.  When I double click on the install exe, it goes through a loading/install screen in wine, then closes automatically.  Afterwards, I navigate to the C>Program Files>Amazon>Kindle For PC>KindleForPC.exe and attempt to run it.

Wine opens for a moment then automatically closes.  Not sure what the issue is.  I've configured/added the Kindle program on the wine menu to load it as Win 98, but it still seems screwy.  I've also attempted it with the older versions of Kindle; no dice.

Any suggestions?

Ubuntu Netbook - 10.10
Wine - 1.2.1

---

### Post by htseb on 2011-01-02
Re: <ericvw's approach>

Worked on an HP1120NR netbook, running 10.04 Lucid Lynx 32-bit.

---

### Post by ellis rowell on 2011-01-27
I've had several tries at running Kindle for PC, no success.

So I've to work around it. Books are downloaded with the Kindle, .pdf's are dragged and dropped when the Kindle is connected to the USB. I now have to work out how I can save maps as .pdf's (it should be easy, get them on screen, print to file as .pdf, then drag and drop).

Ubuntu 10.04

---

### Post by vevel on 2011-01-27
> **ellis rowell said:**
> I've had several tries at running Kindle for PC, no success.

So I've to work around it. Books are downloaded with the Kindle, .pdf's are dragged and dropped when the Kindle is connected to the USB. I now have to work out how I can save maps as .pdf's (it should be easy, get them on screen, print to file as .pdf, then drag and drop).

Ubuntu 10.04

As I said earlier in the thread, I've had no problem with this myself.  Are you running 32-bit Ubuntu?   Have you updated to Wine1.3 ?

---

### Post by nanonils on 2011-02-13
> **erikvw said:**
> After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.

First...

```
[B]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3[/B]
```

Second...

Download Kindle for PC and right mouse click on the file to "open with wine windows program loader".

Excellent! Works out of the box on 10.10 64bit on a X201 Lenovo following the above.

---

### Post by ak331 on 2011-03-13
> **mediamind said:**
> I can confirm this version worked with Lucid (64-bit) running Wine 1.2-rc2.

Thanks I did have the problem umptin time ago before I had to reinstall the OS about 9th time and lost most of the files including this beta and finally I got it working again.

---

### Post by sc4s2cg on 2011-03-24
> **erikvw said:**
> After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.

First...

```
[B]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3[/B]
```

Second...

Download Kindle for PC and right mouse click on the file to "open with wine windows program loader".
I can confirm this works on Ubuntu 10.10 (64bit), using the very latest Kindle PC (v1.4.1, 17.0Mb) just perfectly.

Thank you very much!

---

### Post by whitethunder922 on 2011-04-12
> **erikvw said:**
> After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.

First...

```
[B]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3[/B]
```

Second...

Download Kindle for PC and right mouse click on the file to "open with wine windows program loader".

Worked perfectly for me on 10.10 32-bit, thanks!

---

### Post by nandinga on 2011-05-09
> **erikvw said:**
> After installing wine 1.3 thru apt [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"), I was able to install Kindle using the current KindleForPC-installer.exe (12.3MB version 1.3.0 (30884)) on 10.04. Works fine.

First...

```
[B]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3[/B]
```

Second...

Download Kindle for PC and right mouse click on the file to "open with wine windows program loader".

Working on 11.04 32bit also! Thx erikvw.

---

### Post by g999b on 2011-05-29
Apparently you can also load your kindle books from Calibre. Calibre is a native ubuntu app [http://bit.ly/jYbmmI](http://bit.ly/jYbmmI)
The set up for Kindle is detailed here [http://bit.ly/jbDBfo](http://bit.ly/jbDBfo)

---

### Post by WarrenSensei on 2011-09-06
So, I finally got the old Beta working per the instructions above and several (non-purging) attempts. (Thank you all!)

*However*, there is still a big problem: the very reason I spent the energy and time to do this (already owning and enjoying a Kindle device) was to be able to access the computer-reader-only "Print Replica" versions of books now available. When I go to the Kindle Store and attempt to purchase one, I am asked to install the app. 

I immediately checked my Amazon account and confirmed that the reader app IS in fact registered to my account, so that's not it.

Any ideas?

WINE 1.2.2
Ubuntu 11.04
Chromium 12.0.742.112 (90304)

Thanks!
~Warren

**EDIT:** I don't know how to apply/utilize the "patch" linked to earlier 
([http://bugs2.winehq.org/attachment.cgi?id=24914]("http://bugs2.winehq.org/attachment.cgi?id=24914"))

---

### Post by jzaragoza on 2012-08-12
When I try to install Kindle for PC under 12.04, this is what I get. Any idea?

Unhandled exception: unimplemented function msvcp90.dll.??0?$basic_ifstream@DU?$char_traits@D@std@@@std@@QAE@PB_WHH@Z called in 32-bit code (0x7b839d82).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839d82 ESP:0033f834 EBP:0033f898 EFLAGS:00200287(   - --  I S - -P-C)
 EAX:7b826255 EBX:7b894ff4 ECX:7e073726 EDX:0033f85c
 ESI:80000100 EDI:0033fb5c
Stack dump:
0x0033f834:  0033f8b8 00000008 00000000 80000100
0x0033f844:  00000001 00000000 7b839d82 00000002
0x0033f854:  7e070340 7e073726 00110000 00000000
0x0033f864:  000000ac 02b9ca28 7e0b1ff4 b75e41b9
0x0033f874:  0033f904 000000aa 7bca6ff4 7bc7563b
0x0033f884:  02b9d1a8 02b9d0f0 7b839d3a 02709308
Backtrace:
=>0 0x7b839d82 in kernel32 (+0x29d82) (0x0033f898)
  1 0x7e0702a8 in msvcp90 (+0x402a7) (0x0033f8c8)
  2 0x7e03b66d in msvcp90 (+0xb66c) (0x02b9c064)
  3 0x006bfb69 in kindle (+0x2bfb68) (0x02b9c064)
0x7b839d82: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (146 modules)
PE	  340000-  37d000	Deferred        ssleay32
PE	  390000-  3b9000	Deferred        webcoreviewer
PE	  3c0000-  3d0000	Deferred        pthreadvc2
PE	  3e0000-  3ea000	Deferred        qgif4
PE	  400000- 13cf000	Export          kindle
PE	 13d0000- 14ec000	Deferred        libeay32
PE	 14f0000- 162f000	Deferred        qtscript4
PE	 1630000- 1726000	Deferred        libxml2
PE	 1730000- 1846000	Deferred        javascriptcore
PE	 1850000- 1912000	Deferred        cflite
PE	 1920000- 1aa5000	Deferred        icuin44
PE	 1ab0000- 2053000	Deferred        libwebcore
PE	 2060000- 2106000	Deferred        cairo
PE	 2110000- 214d000	Deferred        libjpeg
PE	 2a20000- 2a53000	Deferred        qjpeg4
PE	10000000-10a34000	Deferred        qtwebkit4
PE	4a800000-4a91f000	Deferred        icuuc44
PE	4ad00000-4bb41000	Deferred        icudt44
PE	5a4c0000-5a4d4000	Deferred        zlib1
PE	61000000-61056000	Deferred        qtxml4
PE	62000000-62093000	Deferred        qtsql4
PE	64000000-640ef000	Deferred        qtnetwork4
PE	65000000-657b8000	Deferred        qtgui4
PE	67000000-67228000	Deferred        qtcore4
ELF	7b800000-7ba29000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba29000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d388000-7d3c6000	Deferred        rsaenh<elf>
  \-PE	7d390000-7d3c6000	\               rsaenh
ELF	7d3c6000-7d3e0000	Deferred        imagehlp<elf>
  \-PE	7d3d0000-7d3e0000	\               imagehlp
ELF	7d3e0000-7d3fe000	Deferred        wintab32<elf>
  \-PE	7d3f0000-7d3fe000	\               wintab32
ELF	7d3fe000-7d411000	Deferred        gnome-keyring-pkcs11.so
ELF	7d511000-7d51a000	Deferred        librt.so.1
ELF	7d51a000-7d51f000	Deferred        libgpg-error.so.0
ELF	7d51f000-7d568000	Deferred        libdbus-1.so.3
ELF	7d568000-7d5ed000	Deferred        libgcrypt.so.11
ELF	7d5ed000-7d6bc000	Deferred        libkrb5.so.3
ELF	7d722000-7d73a000	Deferred        libresolv.so.2
ELF	7d73a000-7d73e000	Deferred        libkeyutils.so.1
ELF	7d73e000-7d750000	Deferred        libp11-kit.so.0
ELF	7d750000-7d762000	Deferred        libtasn1.so.3
ELF	7d762000-7d76b000	Deferred        libkrb5support.so.0
ELF	7d76b000-7d770000	Deferred        libcom_err.so.2
ELF	7d770000-7d798000	Deferred        libk5crypto.so.3
ELF	7d798000-7d7aa000	Deferred        libavahi-client.so.3
ELF	7d7aa000-7d86e000	Deferred        libgnutls.so.26
ELF	7d86e000-7d8ac000	Deferred        libgssapi_krb5.so.2
ELF	7d8ac000-7d8ff000	Deferred        libcups.so.2
ELF	7d93d000-7d971000	Deferred        uxtheme<elf>
  \-PE	7d940000-7d971000	\               uxtheme
ELF	7d971000-7d977000	Deferred        libxfixes.so.3
ELF	7d977000-7d982000	Deferred        libxcursor.so.1
ELF	7d982000-7d990000	Deferred        libavahi-common.so.3
ELF	7d9f4000-7da1e000	Deferred        libexpat.so.1
ELF	7da1e000-7da52000	Deferred        libfontconfig.so.1
ELF	7da52000-7da62000	Deferred        libxi.so.6
ELF	7da62000-7da66000	Deferred        libxcomposite.so.1
ELF	7da66000-7da6f000	Deferred        libxrandr.so.2
ELF	7da6f000-7da79000	Deferred        libxrender.so.1
ELF	7da79000-7da7f000	Deferred        libxxf86vm.so.1
ELF	7da7f000-7da83000	Deferred        libxinerama.so.1
ELF	7da83000-7da8a000	Deferred        libxdmcp.so.6
ELF	7da8a000-7daab000	Deferred        libxcb.so.1
ELF	7daab000-7dab1000	Deferred        libuuid.so.1
ELF	7dab1000-7dacb000	Deferred        libice.so.6
ELF	7dacb000-7dbff000	Deferred        libx11.so.6
ELF	7dbff000-7dc11000	Deferred        libxext.so.6
ELF	7dc11000-7dc1a000	Deferred        libsm.so.6
ELF	7dc1a000-7dcae000	Deferred        winex11<elf>
  \-PE	7dc20000-7dcae000	\               winex11
ELF	7dcae000-7dd48000	Deferred        libfreetype.so.6
ELF	7dd48000-7dd5c000	Deferred        comm.drv16.so
PE	7dd50000-7dd5c000	Deferred        comm.drv16
ELF	7dd5c000-7dd71000	Deferred        system.drv16.so
PE	7dd60000-7dd71000	Deferred        system.drv16
ELF	7dd71000-7de10000	Deferred        krnl386.exe16.so
PE	7dd80000-7de10000	Deferred        krnl386.exe16
ELF	7de10000-7de24000	Deferred        msimg32<elf>
  \-PE	7de20000-7de24000	\               msimg32
ELF	7de24000-7de46000	Deferred        iphlpapi<elf>
  \-PE	7de30000-7de46000	\               iphlpapi
ELF	7de46000-7de61000	Deferred        wsock32<elf>
  \-PE	7de50000-7de61000	\               wsock32
ELF	7de61000-7de94000	Deferred        wintrust<elf>
  \-PE	7de70000-7de94000	\               wintrust
ELF	7de94000-7df4e000	Deferred        crypt32<elf>
  \-PE	7dea0000-7df4e000	\               crypt32
ELF	7df4e000-7df7d000	Deferred        msvcr90<elf>
  \-PE	7df60000-7df7d000	\               msvcr90
ELF	7df7d000-7e00a000	Deferred        msvcrt<elf>
  \-PE	7df90000-7e00a000	\               msvcrt
ELF	7e00a000-7e0ef000	Dwarf           msvcp90<elf>
  \-PE	7e030000-7e0ef000	\               msvcp90
ELF	7e0ef000-7e111000	Deferred        imm32<elf>
  \-PE	7e100000-7e111000	\               imm32
ELF	7e111000-7e203000	Deferred        oleaut32<elf>
  \-PE	7e130000-7e203000	\               oleaut32
ELF	7e203000-7e23d000	Deferred        winspool<elf>
  \-PE	7e210000-7e23d000	\               winspool
ELF	7e23d000-7e31c000	Deferred        comdlg32<elf>
  \-PE	7e240000-7e31c000	\               comdlg32
ELF	7e31c000-7e344000	Deferred        msacm32<elf>
  \-PE	7e320000-7e344000	\               msacm32
ELF	7e344000-7e3f1000	Deferred        winmm<elf>
  \-PE	7e350000-7e3f1000	\               winmm
ELF	7e416000-7e48c000	Deferred        rpcrt4<elf>
  \-PE	7e420000-7e48c000	\               rpcrt4
ELF	7e48c000-7e594000	Deferred        ole32<elf>
  \-PE	7e4a0000-7e594000	\               ole32
ELF	7e594000-7e68d000	Deferred        comctl32<elf>
  \-PE	7e5a0000-7e68d000	\               comctl32
ELF	7e68d000-7e8a0000	Deferred        shell32<elf>
  \-PE	7e6a0000-7e8a0000	\               shell32
ELF	7e8a0000-7e90a000	Deferred        shlwapi<elf>
  \-PE	7e8b0000-7e90a000	\               shlwapi
ELF	7e90a000-7e923000	Deferred        version<elf>
  \-PE	7e910000-7e923000	\               version
ELF	7e923000-7e985000	Deferred        advapi32<elf>
  \-PE	7e930000-7e985000	\               advapi32
ELF	7e985000-7ea42000	Deferred        gdi32<elf>
  \-PE	7e990000-7ea42000	\               gdi32
ELF	7ea42000-7eb82000	Deferred        user32<elf>
  \-PE	7ea50000-7eb82000	\               user32
ELF	7eb82000-7eba8000	Deferred        mpr<elf>
  \-PE	7eb90000-7eba8000	\               mpr
ELF	7eba8000-7ebbe000	Deferred        libz.so.1
ELF	7ebbe000-7ec2d000	Deferred        wininet<elf>
  \-PE	7ebd0000-7ec2d000	\               wininet
ELF	7ec2d000-7ec5f000	Deferred        ws2_32<elf>
  \-PE	7ec30000-7ec5f000	\               ws2_32
ELF	7ec5f000-7ec79000	Deferred        libnsl.so.1
ELF	7ec79000-7ec82000	Deferred        libnss_compat.so.2
ELF	7efc4000-7eff0000	Deferred        libm.so.6
ELF	7eff3000-7f000000	Deferred        libnss_files.so.2
ELF	b74a8000-b74ad000	Deferred        libdl.so.2
ELF	b74ad000-b7652000	Deferred        libc.so.6
ELF	b7653000-b766e000	Deferred        libpthread.so.0
ELF	b766e000-b7672000	Deferred        libxau.so.6
ELF	b7672000-b767e000	Deferred        libnss_nis.so.2
ELF	b767e000-b77c0000	Dwarf           libwine.so.1
ELF	b77c2000-b77e4000	Deferred        ld-linux.so.2
ELF	b77e4000-b77e5000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
0000002e (D) C:\Program Files\Amazon\Kindle\Kindle.exe
	00000030    0
	0000002f    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-29-generic-pae

---

### Post by manoynmonic on 2012-08-12
Dude, there is no need to install kindle for pc anymore.  Just use the Cloud Reader app for Chrome (chromium).  Can read your kindle books offline just fine.

---

### Post by Rob Quee on 2012-10-22
Hi [jzaragoza,]("http://ubuntuforums.org/member.php?u=657578")
I was getting the same error when installing/running Kindle for PC under PlayOnLinux. What fixed it for me was re-installing vcrun2008.

HTH, Cheers
Rob

[U]System Information
[/U]LinuxMint 13 (Maya) i386
WINE 1.4
PlayOnLinux 4.0.14
KindleForPC-installer 47.1MB downloaded today

---

### Post by wildmanne39 on 2012-10-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

