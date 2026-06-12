---
title: "Swedish e-legitimation/BankID installation problem"
date: 2008-10-15
forum: Security
---

### Post by stromdal on 2008-10-15
A question for Swedish users only, I suppose, but here it goes:

I am trying to get a Swedish e-legitimation to work in Ubuntu 8.04, but I have come to a halt. If I'm not mistaken, there are two different ways of getting e-legitimation to work:

1. Install an existing e-legitimation in Firefox; i.e. a certificate that has been obtained on a Windows box and exported to file.
2. Use WinE/IExplore/Nexus Personal.

I obtained an e-legitimation on a WinXP box and exported the certificate to file using "BankID Säkerhetsprogram". The file name is "filename.nge", and when trying to install it in Firefox 3 on Ubuntu, the installation fails with the error message "The PKCS #12 operation failed for unknown reasons."


I also installed WinE and Internet Explorer following this guide: [http://ubuntu.se/wiki/Nordea_e-legitimation](http://ubuntu.se/wiki/Nordea_e-legitimation). When trying to install Nexus Personal, the insatllation fails with the error message "The installation program cannot be used with this version of the operating system. Installation will terminate. Reference 20013"

Any tips on how to solve this?

---

### Post by hyper_ch on 2008-10-15
did you export it from FF3 in windows?

---

### Post by stromdal on 2008-10-15
Nope, that might be worth a try. If I can get the certificate installed in Win/FF.

---

### Post by hyper_ch on 2008-10-15
good luck

---

### Post by RaZoR1394 on 2009-02-23
BankID (Nexus Personal) has native support for Ubuntu 8.04 since early february. Ubuntu 8.04 is the only Linux based system they support officially. I can however use it on Jaunty but not import my certificate generated on a Windows machine. This explains it:

> 
Observera att det inte fungerar att använda ett BankID i en Linux-dator om man har exporterat det från en Windows-dator.
Däremot går det bra att åt andra hållet, från Linux till Windows.
Det går även bra att exportera och importera BankID mellan Mac och Linux åt båda hållen.


According to this, importing a certificate in for ex Ubuntu, generated on a Windows machine won't work (although I've read that some made it). However Linux<->OSX works according to that snippet. Maybe that could mean that Windows->OSX->Linux would be possible? Otherwise I will have to go to the bank and request a new certificate.

If you have an old .p12 certificate it should import no matter what from what I've read. However .nge is more secure and has limitations.

---

### Post by ropeGun on 2009-04-23
Hello, I am am Newbie to Ubuntu...

Actually, I have not installed/started using Ubuntu yet since I am trying to determine if I can do everything that I need to do (and have been able to do in windows).

One of my major hurdles is that I have not been able to determine if it is possible to do my on-line banking within Ubuntu. I need to be able to do my Handelsbanken BankID (Nexus Personal) banking on the Windoze (hopefully, soon to be converted to) Linux machine. I do not dare make the jump to Ubuntu until I know that is is possible to do my on-line banking.

As I (sort of) understand the contents of this thread -- it is possible to do. What I do not understand is how. Is there anyone who can give a step-by-step (on a quite basic level since I do not really understand ID certificates, etc... in Windows) how to make my BankID work from my WindowsXP to Ubuntu 8.10? It will be the same client -- I am planning on blasting away XP completely and doing a clean install with Ubuntu -- does this fact complicate things?

Any input would be very much appreciated.

-john

---

### Post by kisumisu on 2009-06-23
Hi!
To you to know you don't need e-leg to do banking jobs...you can convert your bank id to "engångs koder" its much safer also...you have a card where you have numbers and you enter the number what the bank asks for....works nice with all os that way ;-)

---

### Post by RaZoR1394 on 2009-06-24
One time scratch codes are really annoying in my opinion.

Handelsbanken has a new system where you are using a card reader with an identity card connected either with the reader connected through usb cable to the computer or without. Having the card reader connected through cable does not currently work under Linux as the drivers are lacking but that only limits you to generate your identitification on a file instead of just using the card.

I'm currently using it under Windows and It's very nifty. When using cable you just go to the bank, press the log in link, press authenticate in the upcoming window, then enter your pin code in your card reader and then pressing ok.

Without the cable you should be able to use whatever browser or os you want.

edit:

It seems there are drivers for the card reader afterall!

---

### Post by Granfot on 2009-06-24
> **RaZoR1394 said:**
> One time scratch codes are really annoying in my opinion.

Handelsbanken... <snip>

edit:

It seems there are drivers for the card reader afterall!

Any clues as to how I would go about to get them working under amd64? (I mailed the support earlier, but I figured I might as well ask here too...) 

//Granfot.

---

### Post by zorgzorg2 on 2009-06-29
Hej,

I had exactly the same query... I mailed todos's support this morning about a driver for amd64 arch.

Did you get any feedback ?

---

### Post by Granfot on 2009-06-30
Sorry, I kind of forgot about this... :/

Handelsbanken answered me that they weren't going to support the 64bit arc, and that it was due to problems with the many different flavours of Linux... :P Though I fixed it myself (installed libccid and pcscd as 32bit solved it) and mailed them the solution, they were grateful. :) It's nice to not have the same abilities as the mooks on the other systems already do!

---

### Post by zorgzorg2 on 2009-07-01
I also got an answer, but I wrote to Todos (cardreader manufacturer), and they send me the 64 bits version of the driver.

But I'm still stuck... The cardreader seems to work fine : when I plug it, first I have 
Handelsbanken
====  ======  ======

and then a line on top, so I assume the driver works.

Nexus seems to work ok (passes the bankid test). But when I want to login on the HB site, I got the message that my cardreader isn't plug (which it is actually).

Any clue ?

Also my nexus is empty (no previous e_leg) is this a problem ?
I installed it with nspluginwrapper, that's how I should do it, right ?

Any ideas ?

Thanks,
Zorg

---

### Post by Granfot on 2009-07-01
When I start Nexus, I can see my name there, but I have no previous ID installed, so it's the cardreader that responds. Is pcscd started? try:
```
sudo pcscd --foreground --debug
``` in a terminal window. (You need to stop pcscd first
```
sudo /etc/init.d/pcscd stop
```, if stopping it fails, you didn't start it before trying... That might be the problem.) 
 
If the debug doesn't give any clues, I guess you have to either use the i386 version of pcscd, libccid, nexus personal and the driver, or the problem lies elsewhere. Perhaps you need to get a 64bit version of nexus?
 
If it doesn't work, post the output from the debug here! :)
 
Would you mind sharing the driver in 64-bit with me?
 
Good luck, and thanks in advance! :)

---

### Post by zorgzorg2 on 2009-07-01
It seems pcscd was started.

Here is the output :
```

00000000 debuglog.c:230:DebugLogSetLevel() debug level=debug
00009247 pcscdaemon.c:512:main() pcsc-lite 1.5.4 daemon ready.
00273684 tokenparser.l:175:LTPBundleFindValueWithKey() Value/Key not defined for: ifdVendorID in /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Info.plist
00000370 tokenparser.l:175:LTPBundleFindValueWithKey() Value/Key not defined for: ifdVendorID in /usr/lib/pcsc/drivers/shbecrDeb.bundle/Contents/Info.plist
00054031 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0002
00001883 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00001851 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x05D5, PID: 0x6782
00001120 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x05D5, PID: 0x6782
00001629 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00001853 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x046D, PID: 0xC03E
00001516 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001192 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001127 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001501 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00004822 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0002
00001940 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00002077 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
14122489 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x0B0C, PID: 0x003F
00000027 hotplug_libhal.c:362:HPAddDevice() Adding USB device: usb_device_b0c_3f_noserial_if0
01000643 readerfactory.c:1024:RFInitializeReader() Attempting startup of Handelsbanken card reader 00 00 using /usr/lib/pcsc/drivers/shbecrDeb.bundle/Contents/Linux/libshbecrDeb.so.1.0.0
00037715 readerfactory.c:877:RFBindFunctions() Loading IFD Handler 3.0
	 Todos Data System AB 	
	 Handelbanken card reader 	
	   Version: 1.0.2
00105984 readerfactory.c:249:RFAddReader() Using the pcscd polling thread
00137858 Card ATR: 3B 7D 96 00 00 80 31 80 65 B0 A3 11 00 C8 83 00 00 00 

```

Nothing happens when Nexus starts...
Do you get something more ?

About the driver, I will ask the Todos guy if it’s ok to share it...
Thanks,

---

### Post by zorgzorg2 on 2009-07-01
Hi,

I got the permission to share the file, so here it is:
[http://www.4shared.com/file/115379295/b69ce1f6/SHB_Deb_102_64bit.html](http://www.4shared.com/file/115379295/b69ce1f6/SHB_Deb_102_64bit.html)

Here is the answer I got:
> 
Hi,
 
Yes its ok to share, and since its quite new we would appreciate any feedback.
 
Best regards,


So if you have any comments, send a mail to the support of todos.se.

Cheers,
Zorg

---

### Post by Granfot on 2009-07-01
> **zorgzorg2 said:**
> It seems pcscd was started.

Here is the output :
```

00000000 debuglog.c:230:DebugLogSetLevel() debug level=debug
00009247 pcscdaemon.c:512:main() pcsc-lite 1.5.4 daemon ready.
00273684 tokenparser.l:175:LTPBundleFindValueWithKey() Value/Key not defined for: ifdVendorID in /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Info.plist
00000370 tokenparser.l:175:LTPBundleFindValueWithKey() Value/Key not defined for: ifdVendorID in /usr/lib/pcsc/drivers/shbecrDeb.bundle/Contents/Info.plist
00054031 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0002
00001883 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00001851 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x05D5, PID: 0x6782
00001120 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x05D5, PID: 0x6782
00001629 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00001853 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x046D, PID: 0xC03E
00001516 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001192 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001127 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x045E, PID: 0x00F7
00001501 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00004822 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0002
00001940 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
00002077 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x1D6B, PID: 0x0001
14122489 hotplug_libhal.c:316:get_driver() Looking a driver for VID: 0x0B0C, PID: 0x003F
00000027 hotplug_libhal.c:362:HPAddDevice() Adding USB device: usb_device_b0c_3f_noserial_if0
01000643 readerfactory.c:1024:RFInitializeReader() Attempting startup of Handelsbanken card reader 00 00 using /usr/lib/pcsc/drivers/shbecrDeb.bundle/Contents/Linux/libshbecrDeb.so.1.0.0
00037715 readerfactory.c:877:RFBindFunctions() Loading IFD Handler 3.0
     Todos Data System AB     
     Handelbanken card reader     
       Version: 1.0.2
00105984 readerfactory.c:249:RFAddReader() Using the pcscd polling thread
00137858 Card ATR: 3B 7D 96 00 00 80 31 80 65 B0 A3 11 00 C8 83 00 00 00 

```Nothing happens when Nexus starts...
Do you get something more ?

About the driver, I will ask the Todos guy if it’s ok to share it...
Thanks,

Seems ok, you got just about the same output as I, though I think I now know where the fault lies. Nexus doesn't operate well without the 32bit surroundings... :/ (pcscd and libccid, if we can get a 64bit version of Nexus, I think we are good to go! :) I'll see what I can find...)

> **zorgzorg2 said:**
> Hi,

I got the permission to share the file, so here it is:
[http://www.4shared.com/file/115379295/b69ce1f6/SHB_Deb_102_64bit.html](http://www.4shared.com/file/115379295/b69ce1f6/SHB_Deb_102_64bit.html)

Here is the answer I got:


So if you have any comments, send a mail to the support of todos.se.

Cheers,
Zorg
Thanks! :) I'll look at it once I got a 64bit Nexus to go with the lot... :)

---

### Post by Granfot on 2009-07-01
My mail to Nexus: (Sorry if it appears daft, it's too hot to think right now, and I'm tired... :P ) 

> Hi!

I'm using your Linux version of the Nexus Personal program shipped from Handelsbanken, but they don't provide a 64-bit version, which is why I turn to you. I (and a few other people) are trying to use Nexus and Handelsbanken without the need to force half the system down to 32-bit and the last bit that keeps us from success now is Nexus Personal. 

Is this something you can help us out with? (I do understand that the source is unavailable, but a precompiled amd64-version would be great!) 

Thanks in advance, Mattias and a few more people at ubuntuforums.org 

---

### Post by zorgzorg2 on 2009-07-02
Well, before getting the 64 bits version of the driver, I had the 32 bits version install, with 32b versions of pcscd and libccid, but the problem was the same. 

Maybe I should reinstall nexus. Any pointer to the method you used to install it ?

> **Granfot said:**
> My mail to Nexus: (Sorry if it appears daft, it's too hot to think right now, and I'm tired... :P )

Yeah, it&#8217;s hot. Good we&#8217;ll have rain on the week-end :(

---

### Post by ljungkvist on 2009-07-04
Hi guys,

I'm also following you on this since I want to get rid of having to fire up a complete virtual WinXP each time I want to do some handelsbanken stuff. How did you go about getting the card reader thingy? I've read that they are supposed to do it gradualy over the year, and that you don't _have_ to do anything, just wait. Wonder if there is anything one can do to get it faster?

---

### Post by Granfot on 2009-07-05
> **zorgzorg2 said:**
> Well, before getting the 64 bits version of the driver, I had the 32 bits version install, with 32b versions of pcscd and libccid, but the problem was the same. 

Maybe I should reinstall nexus. Any pointer to the method you used to install it ?



Yeah, it&#8217;s hot. Good we&#8217;ll have rain on the week-end :(

I don't think I did anything in particular, I experimented some with "getlibs", but I don't think anything got changed... :P

> **ljungkvist said:**
> Hi guys,

I'm also following you on this since I want to get rid of having to fire up a complete virtual WinXP each time I want to do some handelsbanken stuff. How did you go about getting the card reader thingy? I've read that they are supposed to do it gradualy over the year, and that you don't _have_ to do anything, just wait. Wonder if there is anything one can do to get it faster?

Either you wait until it comes "naturally", or you can talk to your bank-person and have them order your reader. I think you might be able to do it on your own too, but I'm not sure...

B.T.W. Nothing heard from Nexus yet, not even an acknowledgment that they received my mail...

---

### Post by ljungkvist on 2009-07-21
I now have everything up and working!

A week ago I applied for the reader at the office, and finally today all the different parts have arrived. Then everything went very smoothly. The only thing was I had to use firefox 3.0 to get the driver for the reader. After everything had been installed and worked in 3.0, it now works like a charm in 3.5 also.

Great that this finally works. I was so tired of not being able to do banking in linux. In the end I definately considered switching bank.

---

### Post by Granfot on 2009-10-20
Sorry, totally forgot about this thread, and therefore I haven't posted my shortcomings for a while.

Nexus responded with this:
> 
Hi Mattias,

Thank you for your e-mail and for your point of view. We ask you kindly to also give
your view to BankID via Handelsbanken as it is BankID who order the programme and we develop
it after their wishes and demands on functionality. Therefor it's in BankID's interest to
receive feedback on functionality for the programme.


Kind regards,

Technology Nexus AB

Sofia Lindström
Administration
So today I decided to mail Handelsbanken. I've switched to Gentoo 64 since I've been using Gentoo for several years and feel comfortable with it.

Anyway, here's the mail I'm about to send to Handelsbanken:
> 
Hej!

Har lite problem med att få er kortläsare att fungera med Gentoo Linux. Har tidigare lyckats lösa det i Ubuntu, men även där stötte jag (vi) på lite problem. Alla program och drivrutiner som behöver har vi lyckats få tag på i 64bitars versioner, utom just säkerhetsprogrammet, och då jag mailade till Nexus och bad om hjälp så sa de i stort sett att det inte var något problem, men att det inte var upp till dem, utan er. Skickar en kopia på min konversation med dem och ber er undersöka möjligheterna. Skickar även en länk till forumtråden där vi diskuterat problemet. (Nu var det längesen jag försökte komma någon vart med det här, så tråden är gammal... ) 

Tack på förhand!
/Mattias Granlund.

Länk till forumtråden:[http://ubuntuforums.org/showthread.php?t=948323&highlight=handelsbanken](http://ubuntuforums.org/showthread.php?t=948323&highlight=handelsbanken)

Mailkonversationen:
Hi Mattias,

Thank you for your e-mail and for your point of view. We ask you kindly to also give
your view to BankID via Handelsbanken as it is BankID who order the programme and we develop
it after their wishes and demands on functionality. Therefor it's in BankID's interest to
receive feedback on functionality for the programme.


Kind regards,

Technology Nexus AB

Sofia Lindström
Administration



-----Ursprungligt meddelande-----
Från: [EMAIL="info@nexussafe.com"]info@nexussafe.com[/EMAIL] [mailto:info@nexussafe.com]
Skickat: den 1 juli 2009 21:58
Till: Nx-www
Ämne: Mail från en besökare på Nexus-siten

SENDER: Mattias Granlund (mattias.granlund@gmail.com)

MESSAGE:
Hi!

I'm using your Linux version of the Nexus Personal program shipped from Handelsbanken, but they don't provide a 64-bit version, which is why I turn to you. I (and a few other people) are trying to use Nexus and Handelsbanken without the need to force half the system down to 32-bit and the last bit that keeps us from success now is Nexus Personal.

Is this something you can help us out with? (I do understand that the source is unavailable, but a precompiled amd64-version would be great!)

Thanks in advance, Mattias and a few more people at ubuntuforums.org

MAIL SOURCE: [http://www.nexussafe.com//normal.aspx?id=309&epslanguage=en](http://www.nexussafe.com//normal.aspx?id=309&epslanguage=en)

IP ADDRESS: 213.67.55.18

DATE AND TIME: 7/1/2009 9:58:02 PM
Hopefully they can aid us in getting a precompiled 64bit version of the safetyprogram so that we can use their service. Ubuntu was smooth in the 32bit workings, but Gentoo seems abit harsher, I still haven't figured out how to run a chain of 32bit apps in it... :/

---

### Post by Granfot on 2009-10-21
Well, "Handelsbanken" is as helpful as usual, does anyone here know how to make pcsc-lite and firefox 64bit work with Nexus 32bit app? (In gentoo that is...)

Anyway, here's the response from Handelsbanken:
> 
Hej!

Tyvärr tillhandahåller vi inte 64-bitars versioner av säkerhetsprogrammet. Det grundar sig på att Handelsbanken dessvärre ännu inte stöder 64-bitarssystem i allmänhet när det gäller inloggning med säkerhetsprogrammet. Detta gäller alltså även plattformarna Windows och Mac (även om det för dessa två, med viss reservation, framförallt avser 32-bitars webbläsare).

Linux är ett ständigt växande plattformsalternativ och vi har först nyligen öppnat för dess möjligheter. Plattformen är mycket mer varierad än de två andra marknadsdominerande och det föranleder att vi måste hålla någon form av "strömlinjeformade" systemkrav. Hur vi kommer att utveckla stödet för Linux framöver kan jag i dagsläget inte ge en uppskattning på.


Handelsbankens internettjänster skall fungera enligt nedanstående paketeringar:

A. Kortläsare med sladd / Handelsbankens e-legitimation
Linux-kernel 2.6.24 och senare.
Ubuntu 8.04 eller högre, enbart 32-bitars version.
Gnome/KDE skrivbordsmiljö.

Webbläsare
Firefox 3.0.6 eller högre.

Säkerhetsprogram
BankID Säkerhetsprogram 4.10.2.16 eller högre.

Drivrutin för inloggningssätt Kortläsare med sladd måste vara installerad.


Java (enbart för inloggning mot tillförlitandet parter, Skatteverket, CSN, Försäkringskassan och så vidare).
Java 6 uppdatering 13 eller högre (krav enbart för BankID på fil).


B. Kortläsare utan sladd / Användarnamn
Alla Linux-distributioner med internetanslutning.



________________________________

Du är även välkommen att kontakta oss på telefon:
Privatkund 0771-596060
Företagskund 0771-234000

Ytterligare information hittar du på [www.handelsbanken.se/hjalp]("http://www.handelsbanken.se/hjalp")

Med vänlig hälsning
Handelsbanken Kundsupport

Magnus


Also, I forgot... Can anyone reshare the 64bit driver for the cardreader? Mine was lost in a harddrive failure, and the link doesn't seem to work anymore... :/

---

### Post by dralbin82 on 2009-12-24
I'm really interested in the 64 bit version of the nexus personal also.

I have forced the 32 bit version to install but get an error from Firefox when it attempts to load:

LoadPlugin: failed to initialize shared library /usr/local/lib/personal/libplugins.so [/usr/local/lib/personal/libplugins.so: wrong ELF class: ELFCLASS32]

//Albin

---

### Post by dralbin82 on 2009-12-29
Oh, I didn't read the thread good enough. I used the nspluginwrapper and it worked fine. 

Then a problem arised with the PKCS#11 libP11.so but it turned out it's not needed as you could just import the p12 certificate in firefox and then it works. But now I don't have any password protection for the certificate so I can log in to Handelsbanken without writing my password. :)

---

### Post by Holmen on 2010-01-19
I also would like the 64-bit version of Nexus Personal to be re-shared.

---

### Post by nidelius on 2010-02-18
Finaly got it working!

Thanx albin for the tip with importing the cert in FF
Have the same security as you now ;D

---

### Post by dralbin82 on 2010-02-19
Great! 

If you want the card reader to work aswell you can have a look at this thread:
[http://ubuntu.se/showthread.php/8631-Handelsbanken-inloggning-dosa-med-sladd-i-Ubuntu-9.10-64-bit?p=39517](http://ubuntu.se/showthread.php/8631-Handelsbanken-inloggning-dosa-med-sladd-i-Ubuntu-9.10-64-bit?p=39517)

I've done the steps there to get the 32 bit driver to work under 64 bit Ubuntu. Now everything works as good as on Windows :D

//Albin

---

### Post by aliswe on 2012-09-21
Det har inte ett skit att göra med att linuxdistributionerna skulle vara "varierande", som de själva säger stödjer ju inte programmet 64bitars miljöer alls. Någonstans.

Dessutom måste det ju vara kodat av de mest inkompetenta klåparna i historien med tanke på hur jävla dåligt skiten fungerar så att det inte sker någon utveckling är ju inte heller konstigt.

Deras egen guide över kända fel (som inte involverar sådant jag har problem med) var en PDF på 18 sidor ..


For whatever reason I don't get that **** to validate atm (using real bankid and nspluginwrapper.)

I don't know why. I've removed most extensions and other plugins.

---

### Post by aliswe on 2012-09-21
För openSUSE 12.2 så gäller som vanligt att packa upp BISP, gå till katalogen och köra sudo ./install<version> i.

Sedan behövs nspluginwrapper och libpng version 12 i 32-bitsversion som installeras med:

sudo zypper install nspluginwrapper libpng12-0-32bit

Gå sedan till ~/.mozilla/plugins som din användare och kör:
nspluginwrapper -i /usr/local/lib/personal/libplugins.so

Sedan skall det vara klart.



För att kunna ladda ner programmet och göra versionskontrollen på websidan behöver du ljuga om vilken plattform du kör, det gör du genom att installera:
[https://addons.mozilla.org/sv-se/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/sv-se/firefox/addon/user-agent-switcher/)
Gå sedan till Tools -> Default User Agent -> Edit User Agents..
Klicka på New -> New User Agent, ersätt x86_64 med i686 överallt och välj ok. Döp den till Mozilla i686 eller något.
Gå sedan till Tools -> Default User Agent och välj din hemmasnickrade user-agent där. Den verkar återställas till standardinställningen vid omstart av webläsaren. Går kanske att göra permanent om man skulle vilja det.

---

### Post by aliswe on 2012-09-21
Om det är (bl.a.) Handelsbanken som beställer tjänsten av Nexus föreslår jag att de istället betalar en slant till skaparen/skaparna av fribid för att göra samma sak.

Deras klient fungerar i de flesta fallen och är open-source och går finfint att bygga i 64bitars version av operativsystemet. Med rätt dokumentation hade den säkert fungerat perfekt. Änsålänge har de fått in dryga 8000 kr i donationer för sitt program och det är ju gissningsvis bra mycket mindre än vad Nexus har tagit för sitt som fungerar skitdåligt och inte överallt och inte är open-source.

Huvudsaken är ju att säkerhetstänket och lösningen är korrekt och inte att källkoden är stängd.

---

### Post by overdrank on 2012-09-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

