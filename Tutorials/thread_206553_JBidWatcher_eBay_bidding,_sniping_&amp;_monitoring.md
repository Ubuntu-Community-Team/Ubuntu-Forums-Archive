---
title: "JBidWatcher: eBay bidding, sniping &amp; monitoring software for all"
date: 2006-06-30
forum: Tutorials
---

### Post by stani on 2006-06-30
**[SIZE="4"]Introduction[/SIZE]**

As the [jbidwatcher howto for Ubuntu 5.10]("http://www.ubuntuforums.org/showthread.php?t=95370") got outdated, I post a new howto for Lucid. However I'd like to thank foxy123 for his initial howto and he deserves the credits.


**[SIZE="4"]jBidWatcher[/SIZE]**

From the [jBidWatcher website]("http://http://www.jbidwatcher.com/"):
> A Java-based application allowing you to monitor auctions you're not part of, submit bids, snipe (bid at the last moment), and otherwise track your auction-site experience. It includes adult-auction management, MANY currencies (yen, pound, dollar (US, Canada, Australian, and New Taiwanese), Swiss Francs, and euro, presently), drag-and-drop of auction URLs, a unique and powerful 'multisniping' feature, a relatively nice UI

You need the latest release as the older ones are not able to communicate with ebay anymore. In case there is a new version, let me know and I'll update this howto.About this version:
> I&#8217;ve finally released 2.1 (followed quickly by a 2.1.1 release). This is my &#8216;perfect is the enemy of good&#8217; release. :) While there are probably bugs I&#8217;ve missed, I tested it pretty heavily

To install jBidWatcher, just copy these statements in a shell:
```
sudo mkdir /usr/local/share/java
cd /usr/local/share/java
sudo wget http://assets1.jbidwatcher.com/images/jay_noback.png
sudo wget http://www.jbidwatcher.com/download/JBidwatcher-2.1.1.jar
sudo gedit /usr/local/bin/jbidwatcher
```

This will open a text editor, paste the following text:
```
#!/bin/sh
java -jar /usr/local/share/java/JBidwatcher-2.1.1.jar

```

Now make this script executable:

```
sudo chmod +x /usr/local/bin/jbidwatcher
```

This will allow you to start jbidwatcher from the terminal with:

```
jbidwatcher
```


**[SIZE="4"]Sun Java[/SIZE]**

In order to use jBidWatcher you need to install sun-java. JBidWatcher doesn't work with another version of Java! You can find more info about installing sun-java here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

To be short: if you have the multiverse repositories enabled, you can install it like this:

```
sudo apt-get install sun-java6-bin
```

...and make sure it is the default:

```
sudo update-alternatives --config java
```

> $ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/jvm/java-gcj/jre/bin/java
      2        /usr/bin/gij-wrapper-4.1
      3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

**[SIZE="4"]Menu entry[/SIZE]**

Paste the following in the terminal:
```
sudo gedit /usr/share/applications/jBidWatcher.desktop
```

```
[Desktop Entry]
Comment=eBay bidding, sniping & monitoring
Name=jBidWatcher
Exec=jbidwatcher
Terminal=false
Encoding=UTF-8
Type=Application
Icon=/usr/local/share/java/jay_noback.png
Categories=Network
```

**[SIZE="4"]Background[/SIZE]**

If you wonder why to use this tool, read these articles:
[On Ebay, it pays to snipe]("http://www.usatoday.com/tech/science/columnist/2006-06-25-physics-of-ebay_x.htm")
[How to win on Ebay: snipe!]("http://slashdot.org/articles/06/06/26/1812238.shtml")

---

### Post by philbridges on 2006-07-08
Thanks so much of the step by step instructions, I thought Linspire was good but ubuntu is so much easier!  I've followled your instructions but keep seeing the following error..

phil@BamBam:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate
phil@BamBam:~$

Being a newbie it makes no sense to me, just wondered if I'd expect such an error?

Thanks

Thanks

---

### Post by stani on 2006-07-08
> **philbridges said:**
> 
E: Package sun-j2re1.5 has no installation candidate

Being a newbie it makes no sense to me, just wondered if I'd expect such an error?

Ubuntu installs it packages from repositories. You don't seem to have a repository with sun java by default. Therefore you could use the PLF repositories. I've updated my HowTo so you can follow the instructions under Sun Java again.

Good luck,
Stani

---

### Post by diepruis on 2006-07-08
> **stani said:**
> 
If you wonder why to use this tool, read these articles:
[On Ebay, it pays to snipe]("http://http://www.usatoday.com/tech/science/columnist/2006-06-25-physics-of-ebay_x.htm")
[How to win on Ebay: snipe!]("http://http://slashdot.org/articles/06/06/26/1812238.shtml")

You made a mistake with the URLs above. They should be:

[On Ebay, it pays to snipe]("http://www.usatoday.com/tech/science/columnist/2006-06-25-physics-of-ebay_x.htm")
[How to win on Ebay: snipe!]("http://slashdot.org/articles/06/06/26/1812238.shtml")

Just thought I'd give you a heads up.

---

### Post by stani on 2006-07-11
Thanks, I fixed the links.
Stani

---

### Post by meander on 2006-07-21
i cant seem to get it working, the install procedure goes without error, but i get no menu entry after, and if i just try to run jbidwatcher i get permisson denied, but sudo jbidwatcher gives an unknown command error :-k

---

### Post by codypumper on 2006-07-21
I get the exact same responses as meander.

---

### Post by chadk on 2006-08-11
Here's the error I get:
```
jbidwatcher
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at JBidWatch.main(JBidWatch.java:602)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more

```


You guys with the permission error do this:
sudo chmod 777 /usr/local/bin/jbidwatcher

---

### Post by stani on 2006-08-19
I've updated the howto (making script executable+java package). I just installed jbidwatcher on another computer and it worked fine. Are you sure you configured sun-java as the default java with this command:

```
sudo update-alternatives --config java
```

---

### Post by rko618 on 2006-08-19
I can't find Jbidwatcher in my menu so I ran it from the command line and I got this
```
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

```

I'm guessing this is why jBidWatcher looks so ugly.  I checked and I have ubuntulooks installed so I don't know how to fix this.

---

### Post by hanzj on 2006-08-19
thanks for the howto. 
I'm having problems with Right-click on Item/"Show in Browser". It go to my browser, but a window pops up with the following:

Server: local
Message: JBidwatcher

it asks for my username and password. I then enter my ebay username and password, but it doesn't show. The URL is something like:

[http://localhost:9099/200018322053](http://localhost:9099/200018322053)
and the message in the browser window is:
"Access to this server is denied without an account."

What's wrong?

---

### Post by synd7 on 2006-08-20
Sniping software ruins ebay, it makes it too easy cheat:evil: 

For this i thank you:-D 
No more losing in the last 0.5 seconds

---

### Post by stani on 2006-08-21
@hanzj
I have no clue. In the File>Configure>Ebay you can set Browse to the ebay of your liking. Maybe that helps.

Stani

---

### Post by hanzj on 2006-08-21
@stani,
nope, it's set up right there. Even without looking, I had already thought that the problem isn't there. Because if that was the problem, I don't think Jbidwatcher would be able to do anything else, such as pulling in the info and sniping for me.

Does RightClick/'Show In Browser' work for you all?

---

### Post by stani on 2006-08-21
It works for me perfectly. However if you start jBidWatcher with alltray, it does not work.

---

### Post by PowerRanger on 2006-08-24
> **hanzj said:**
> thanks for the howto. 
I'm having problems with Right-click on Item/"Show in Browser". It go to my browser, but a window pops up with the following:

Server: local
Message: JBidwatcher

it asks for my username and password. I then enter my ebay username and password, but it doesn't show. The URL is something like:

[http://localhost:9099/200018322053](http://localhost:9099/200018322053)
and the message in the browser window is:
"Access to this server is denied without an account."

What's wrong?


What browser is it using?  I set mine to 'mozilla',  'firefox' also seems to work.  This is under the configuration tab  Browser | Linux command:.

Mike

---

### Post by hanzj on 2006-08-24
Hi, Mike! It's using opera, which is my preferred browser.

---

### Post by PowerRanger on 2006-08-24
What happens if you use another browser?

---

### Post by jimmymac on 2006-08-25
Alright guys,

I get the following error when I try to sync with My Ebay:

Fri Aug 25 16:12:34 BST 2006: Loading page: [http://my.ebay.com/ws/eBayISAPI.dll?MyeBay&CurrentPage=MyeBayBidding](http://my.ebay.com/ws/eBayISAPI.dll?MyeBay&CurrentPage=MyeBayBidding)
Fri Aug 25 16:12:36 BST 2006: PMQ Caught exception: XMLParseException: XML Parse Exception during parsing of a input-tag at line 1: Value missing for attribute with key "disabled"
XMLParseException: XML Parse Exception during parsing of a input-tag at line 1: Value missing for attribute with key "disabled"
        at XMLElement.valueMissingForAttribute(XMLElement.java:1368)
        at XMLElement.scanOneAttribute(XMLElement.java:1003)
        at XMLElement.scanAttributes(XMLElement.java:727)
        at XMLElement.parseCharArray(XMLElement.java:623)
        at XMLElement.parseCharArray(XMLElement.java:605)
        at XMLElement.parseString(XMLElement.java:537)
        at JHTML$Form.addInput(JHTML.java:160)
        at JHTML.addToken(JHTML.java:252)
        at JHTMLParser.addToken(JHTMLParser.java:202)
        at JHTMLParser.parse(JHTMLParser.java:129)
        at JHTMLParser.<init>(JHTMLParser.java:41)
        at JHTML.<init>(JHTML.java:43)
        at SpecificAuction.preParseAuction(SpecificAuction.java:38)
        at AuctionServer.loadAuction(AuctionServer.java:662)
        at AuctionServer.addAuction(AuctionServer.java:549)
        at AuctionEntry.prepareAuctionEntry(AuctionEntry.java:257)
        at AuctionEntry.<init>(AuctionEntry.java:302)
        at AuctionsManager.newAuctionEntry(AuctionsManager.java:320)
        at JBWDropHandler.messageAction(JBWDropHandler.java:48)
        at PlainMessageQueue.run(PlainMessageQueue.java:70)
        at java.lang.Thread.run(Thread.java:595)
Fri Aug 25 16:12:37 BST 2006: No items on page!


Any ideas?

MTIA

Jimmy

---

### Post by OrganicPanda on 2006-08-25
Everything worked fine, I got the:

```

/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

```

but java programs are always ugly, Cheers for the how-to

---

### Post by scwalla on 2006-08-25
> **jimmymac said:**
> Alright guys,

I get the following error when I try to sync with My Ebay:

Fri Aug 25 16:12:34 BST 2006: Loading page: [http://my.ebay.com/ws/eBayISAPI.dll?MyeBay&CurrentPage=MyeBayBidding](http://my.ebay.com/ws/eBayISAPI.dll?MyeBay&CurrentPage=MyeBayBidding)
Fri Aug 25 16:12:36 BST 2006: PMQ Caught exception: XMLParseException: XML Parse Exception during parsing of a input-tag at line 1: Value missing for attribute with key "disabled"
XMLParseException: XML Parse Exception during parsing of a input-tag at line 1: Value missing for attribute with key "disabled"
        at XMLElement.valueMissingForAttribute(XMLElement.java:1368)
        at XMLElement.scanOneAttribute(XMLElement.java:1003)
        at XMLElement.scanAttributes(XMLElement.java:727)
        at XMLElement.parseCharArray(XMLElement.java:623)
        at XMLElement.parseCharArray(XMLElement.java:605)
        at XMLElement.parseString(XMLElement.java:537)
        at JHTML$Form.addInput(JHTML.java:160)
        at JHTML.addToken(JHTML.java:252)
        at JHTMLParser.addToken(JHTMLParser.java:202)
        at JHTMLParser.parse(JHTMLParser.java:129)
        at JHTMLParser.<init>(JHTMLParser.java:41)
        at JHTML.<init>(JHTML.java:43)
        at SpecificAuction.preParseAuction(SpecificAuction.java:38)
        at AuctionServer.loadAuction(AuctionServer.java:662)
        at AuctionServer.addAuction(AuctionServer.java:549)
        at AuctionEntry.prepareAuctionEntry(AuctionEntry.java:257)
        at AuctionEntry.<init>(AuctionEntry.java:302)
        at AuctionsManager.newAuctionEntry(AuctionsManager.java:320)
        at JBWDropHandler.messageAction(JBWDropHandler.java:48)
        at PlainMessageQueue.run(PlainMessageQueue.java:70)
        at java.lang.Thread.run(Thread.java:595)
Fri Aug 25 16:12:37 BST 2006: No items on page!


Any ideas?


MTIA

Jimmy

Me too!  I can't load from MyEbay, searches don't work, can't even add a new auction manually.  I also get the following errors at start-up:

/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
Fri Aug 25 12:10:05 EDT 2006: Getting the sign in cookie. [mist-net@ebay: Error communicating with server/25-Aug-2006 12:10:04 EDT]

I'm guessing that "Error communicating with server" is not good!

Is Jbidwatcher currently working for anyone?

---

### Post by treborblack on 2006-08-28
Thanks for the tutorial, the proggy works a treat:p 
however on my install on the menu its shown up under lost and found. how do i correct that?

---

### Post by stani on 2006-08-28
> **treborblack said:**
> Thanks for the tutorial, the proggy works a treat:p 
however on my install on the menu its shown up under lost and found. how do i correct that?
I think I forgot to add "Categories=Network" to the desktop file. I updated my first post, so you can copy & paste from there.

> **scwalla said:**
> Me too!  I can't load from MyEbay, searches don't work, can't even add a new auction manually.  I also get the following errors at start-up:

/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

You can ignore these messages. They appear for me as well.
> 
Fri Aug 25 12:10:05 EDT 2006: Getting the sign in cookie. [mist-net@ebay: Error communicating with server/25-Aug-2006 12:10:04 EDT]

I'm guessing that "Error communicating with server" is not good!

Is Jbidwatcher currently working for anyone?
Yes it does. Are you sure your username and password are set correctly and that you are using SUN java?

---

### Post by Quid on 2007-09-09
I have yet to install this on my new Ubuntu install ( feisty), but I thought my research would help others.
[http://www.jbidwatcher.com/]("http://www.jbidwatcher.com/")
 is the link for the origin of JBidWatcher.

They note that there is a new version to take into account ebay changing formats - excerpt:
[I]
News Flash (August 11, 2007) -- JBidwatcher 1.0.2 is released.
This version fixes the multiple breakages eBay introduced over the last few weeks, including changing the title format, removing (then adding back) the end date, and start date, many changes to different listing types, the change of the official time server URL,[/I]

This may account for the flurry of issues - 

Does anyone know if the mutliverse packages have been updated? 

Ubuntu Rules!
Bruce from Canada

---

### Post by An85Zk9tc8rfjV8i on 2009-02-04
> **stani said:**
> **[SIZE="4"]Introduction[/SIZE]**

As the [jbidwatcher howto for Ubuntu 5.10]("http://www.ubuntuforums.org/showthread.php?t=95370") got outdated, I post a new howto for dapper & edgy. However I'd like to thank foxy123 for his initial howto and he deserves the credits.


**[SIZE="4"]jBidWatcher[/SIZE]**

From the [jBidWatcher website]("http://http://www.jbidwatcher.com/"):


You need the latest release as the older ones are not able to communicate with ebay anymore. In case there is a new version, let me know and I'll update this howto.About this version:

JBidwatcher 2.0beta11, a critical bugfix version, is available
[http://www.jbidwatcher.com/download/JBidwatcher-2.0beta11.jar](http://www.jbidwatcher.com/download/JBidwatcher-2.0beta11.jar)

Java Downloads for Linux
Recommended Version 6 Update 11
[http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp)

synaptic :
search : "sun java" for sun-java6-jre

---

### Post by nova47 on 2009-02-15
For the newbies like me:

They're now on version 2.0 so instead of typing:
sudo wget [http://www.jbidwatcher.com/download/JBidWatcher-1.0.jar](http://www.jbidwatcher.com/download/JBidWatcher-1.0.jar)

Type

sudo wget [http://www.jbidwatcher.com/download/JBidwatcher-2.0.jar](http://www.jbidwatcher.com/download/JBidwatcher-2.0.jar)

For some reason the W was changed to a w which threw me off a bit :-D

This has already been mentioned but they've also updated to java v.6 so chances are you won't need to install the java in the walkthrough. I suggest you check /usr/local/share/java$ sudo update-alternatives --config java before you install any new java. Chances are (particularly if you do any programming) you'll already have an entry that says something like this

/usr/lib/jvm/java-6-sun/jre/bin/java

Just make that your default and it will run just fine. If you don't have it you can find it in the synaptic packet manager. I also just discovered that jbidwatcher itself is now in the synaptic package manager if you want to save yourself some trouble.

---

### Post by raddad on 2009-04-19
Ok, I followed these instructions *except* I skipped the java portion because I have java working. (and current jbid is 2.0.2)  The menu shows jbidwatcher but nothing happens when I select it.

So I went to the java config part, selected what looked close to what you suggested:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/lib/jvm/java-gcj/jre/bin/java
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java

I chose #5.

Still nothing happens.

Any suggested fixes?  Where did I goof?



> **stani said:**
> **[SIZE="4"]Introduction[/SIZE]**

As the [jbidwatcher howto for Ubuntu 5.10]("http://www.ubuntuforums.org/showthread.php?t=95370") got outdated, I post a new howto for dapper & edgy. However I'd like to thank foxy123 for his initial howto and he deserves the credits.


**[SIZE="4"]jBidWatcher[/SIZE]**

From the [jBidWatcher website]("http://http://www.jbidwatcher.com/"):


You need the latest release as the older ones are not able to communicate with ebay anymore. In case there is a new version, let me know and I'll update this howto.About this version:


To install jBidWatcher, just copy these statements in a shell:
```
sudo mkdir /usr/local/share/java
cd /usr/local/share/java
sudo wget http://www.jbidwatcher.com/jbidwatch.jpg
sudo wget http://www.jbidwatcher.com/download/JBidWatcher-1.0.jar
sudo gedit /usr/local/bin/jbidwatcher
```

This will open a text editor, paste the following text:
```
#!/bin/sh
java -jar /usr/local/share/java/JBidWatcher-1.0.jar

```

Now make this script executable:

```
sudo chmod +x /usr/local/bin/jbidwatcher
```


**[SIZE="4"]Sun Java[/SIZE]**

In order to use jBidWatcher you need to install sun-java. JBidWatcher doesn't work with another version of Java! You can find more info about installing sun-java here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

To be short: if you have the multiverse repositories enabled, you can install it like this:

```
sudo apt-get install sun-java5-bin
```

...and make sure it is the default:

```
sudo update-alternatives --config java
```



**[SIZE="4"]Menu entry[/SIZE]**

Paste the following in the terminal:
```
gedit ~/.local/share/applications/jBidWatcher.desktop
```

```
[Desktop Entry]
Comment=eBay bidding, sniping & monitoring
Name=jBidWatcher
Exec=jbidwatcher
Terminal=false
Encoding=UTF-8
Type=Application
Icon=/usr/local/share/java/jbidwatch.jpg
Categories=Network
```

**[SIZE="4"]Background[/SIZE]**

If you wonder why to use this tool, read these articles:
[On Ebay, it pays to snipe]("http://www.usatoday.com/tech/science/columnist/2006-06-25-physics-of-ebay_x.htm")
[How to win on Ebay: snipe!]("http://slashdot.org/articles/06/06/26/1812238.shtml")

---

### Post by charonred on 2009-12-17
I've just installed jbidwatcher 1.0.2 via Synaptic in Hardy 8.04.3

Soon as I ran it, I was informed of a newer version which I have now downloaded 

JBidwatcher-2.1pre4.jar

but I don't know how to install from a .jar

---

### Post by for56gt on 2009-12-22
Sniping issue : when sniping a higher price than the winning bidder I do not obtain the item.
Under the "complete" tab my price is preceded by a little  star (or asterik).
Does one knows what it means? Thank You

---

### Post by sdowney717 on 2010-01-02
"but I don't know how to install from a .jar"

jar is just the binary. you run it with a java command line
java -jar name.jar

so like this in the directory where the jar file is located
java -jar JBidwatcher-2.1pre4.jar

---

### Post by mysterious_beans on 2010-04-21
> **charonred said:**
> I've just installed jbidwatcher 1.0.2 via Synaptic in Hardy 8.04.3

Soon as I ran it, I was informed of a newer version which I have now downloaded 

JBidwatcher-2.1pre4.jar

but I don't know how to install from a .jar

If you are following the original recipe, you just need to change the script (at */usr/local/bin/jbidwatcher*) that launches Java and executes the contents of the jar (Java archive). Inside that script, it refers to the jar file -- change the filename to match the jar file you downloaded (the most recent version, most likely).

Also, for those having issues installing sun-java with *apt-get*, try using *synaptic* instead; in my case, I was able to install *sun-java6-bin*/*sun-java6-jre* instead of version 5.

Finally, the location of the files in the original recipe has changed (or maybe was initially wrong); to get the bluejay picture that will become an icon on your menu, just visit the *jbidwatcher* main site, and examine the properties of the picture in the top-left; it will reveal the path you can pass to *wget* to retrieve the picture, or you can just right-click-save-as and place the picture file in the appropriate spot (as described in the recipe).

P.S. Once the upgrade is complete and everything is working, you can go into */usr/local/share/java* and delete older-version jar files since they are no longer needed.

---

### Post by stani on 2010-08-28
I've updated the instructions to the latest version.

---

### Post by jaimito on 2010-10-25
Just to say it works perfectly for me. Check Sun Java installed first, check system is OK. Just works.

:guitar:

tyvm

---

### Post by Phkillah on 2010-11-05
.deb .deb .deb .deb .deb..........

---

### Post by divers3 on 2010-11-30
> **Phkillah said:**
> .deb .deb .deb .deb .deb..........

Yah, a *.deb package would be really helpful for newbies & fat fingered folks such as myself.](*,)

---

### Post by TheTank on 2010-12-02
Personally a feature I'd really like to see is the software running as a service and providing a web interface so that I can slap it on my 24/7 server and control it from the network.

---

### Post by FLCL on 2011-02-04
For the newest version 2.1.3, i simply changed "2.1.1" to "2.1.3" and it downloaded fine and everything but when I try to run it I get```
Unable to access jarfile /usr/local/share/java/JBidwatcher-2.1.3.jar

```. What gives? I've even tried running with sudo, same error

---

### Post by QBX on 2011-02-17
Hi, I have succesfully installed JBidWatcher on my previous laptop and on another computer.

Right now I am having trouble getting it to run on an IBM laptop, Core i7 Processor with 64-bit Ubuntu 10.10. I would appreciate some help.

When I launch JBidWatcher, I get it to the point where it says loading auctions, but sticks at that point.

Here is the output I get if launched from a terminal:


```
Fri Feb 18 00:52:07 GMT 2011: JBidwatcher 2.1.3-
Fri Feb 18 00:52:07 GMT 2011: Sun Microsystems Inc. Java, version 1.6.0_22 on Linux
Fri Feb 18 00:52:07 GMT 2011: Logging to /home/username/.jbidwatcher/errors.9.log
Fri Feb 18 00:52:08 GMT 2011: Upgrading error
java.sql.SQLException: Failed to create database 'jbdb', see the next exception for details.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.newEmbedSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.seeNextException(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.createDatabase(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.<init>(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection30.<init>(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection40.<init>(Unknown Source)
	at org.apache.derby.jdbc.Driver40.getNewEmbedConnection(Unknown Source)
	at org.apache.derby.jdbc.InternalDriver.connect(Unknown Source)
	at org.apache.derby.jdbc.AutoloadedDriver.connect(Unknown Source)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:154)
	at com.jbidwatcher.util.db.Database.setup(Database.java:92)
	at com.jbidwatcher.util.db.Database.<init>(Database.java:53)
	at com.jbidwatcher.Upgrader.upgrade(Upgrader.java:26)
	at com.jbidwatcher.app.JBidWatch.main(JBidWatch.java:441)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.simontuffs.onejar.Boot.run(Boot.java:306)
	at com.simontuffs.onejar.Boot.main(Boot.java:159)
Caused by: java.sql.SQLException: Failed to create database 'jbdb', see the next exception for details.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.wrapArgsForTransportAcrossDRDA(Unknown Source)
	... 22 more
Caused by: java.sql.SQLException: Directory /home/username/.jbidwatcher//home/username/.jbidwatcher/jbdb already exists.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.wrapArgsForTransportAcrossDRDA(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.generateCsSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.TransactionResourceImpl.wrapInSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.TransactionResourceImpl.handleException(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.handleException(Unknown Source)
	... 19 more
Caused by: ERROR XBM0J: Directory /home/username/.jbidwatcher//home/username/.jbidwatcher/jbdb already exists.
	at org.apache.derby.iapi.error.StandardException.newException(Unknown Source)
	at org.apache.derby.impl.services.monitor.StorageFactoryService$9.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.derby.impl.services.monitor.StorageFactoryService.createServiceRoot(Unknown Source)
	at org.apache.derby.impl.services.monitor.BaseMonitor.bootService(Unknown Source)
	at org.apache.derby.impl.services.monitor.BaseMonitor.createPersistentService(Unknown Source)
	at org.apache.derby.iapi.services.monitor.Monitor.createPersistentService(Unknown Source)
	... 19 more
Fri Feb 18 00:52:10 GMT 2011: Scripting is not enabled.
Fri Feb 18 00:52:10 GMT 2011: JBidwatcher: java.lang.RuntimeException: Can't access the auctions database table
java.lang.RuntimeException: Can't access the auctions database table
	at com.jbidwatcher.util.db.ActiveRecord.openDB(ActiveRecord.java:32)
	at com.jbidwatcher.auction.AuctionInfo.getRealDatabase(AuctionInfo.java:504)
	at com.jbidwatcher.auction.AuctionInfo.getDatabase(AuctionInfo.java:501)
	at com.jbidwatcher.util.db.ActiveRecord.count(ActiveRecord.java:63)
	at com.jbidwatcher.auction.AuctionInfo.count(AuctionInfo.java:531)
	at com.jbidwatcher.ui.AuctionsManager.loadAuctionsFromDatabase(AuctionsManager.java:222)
	at com.jbidwatcher.app.JBidWatch.<init>(JBidWatch.java:628)
	at com.jbidwatcher.app.JBidWatch.main(JBidWatch.java:485)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.simontuffs.onejar.Boot.run(Boot.java:306)
	at com.simontuffs.onejar.Boot.main(Boot.java:159)
Caused by: java.sql.SQLException: Failed to create database 'jbdb', see the next exception for details.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.newEmbedSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.seeNextException(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.createDatabase(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.<init>(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection30.<init>(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection40.<init>(Unknown Source)
	at org.apache.derby.jdbc.Driver40.getNewEmbedConnection(Unknown Source)
	at org.apache.derby.jdbc.InternalDriver.connect(Unknown Source)
	at org.apache.derby.jdbc.AutoloadedDriver.connect(Unknown Source)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:154)
	at com.jbidwatcher.util.db.Database.setup(Database.java:92)
	at com.jbidwatcher.util.db.Database.<init>(Database.java:53)
	at com.jbidwatcher.util.db.Table.<init>(Table.java:57)
	at com.jbidwatcher.util.db.ActiveRecord.openDB(ActiveRecord.java:29)
	... 13 more
Caused by: java.sql.SQLException: Failed to create database 'jbdb', see the next exception for details.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.wrapArgsForTransportAcrossDRDA(Unknown Source)
	... 29 more
Caused by: java.sql.SQLException: Directory /home/username/.jbidwatcher//home/username/.jbidwatcher/jbdb already exists.
	at org.apache.derby.impl.jdbc.SQLExceptionFactory.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.wrapArgsForTransportAcrossDRDA(Unknown Source)
	at org.apache.derby.impl.jdbc.SQLExceptionFactory40.getSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.Util.generateCsSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.TransactionResourceImpl.wrapInSQLException(Unknown Source)
	at org.apache.derby.impl.jdbc.TransactionResourceImpl.handleException(Unknown Source)
	at org.apache.derby.impl.jdbc.EmbedConnection.handleException(Unknown Source)
	... 26 more
Caused by: ERROR XBM0J: Directory /home/username/.jbidwatcher//home/username/.jbidwatcher/jbdb already exists.
	at org.apache.derby.iapi.error.StandardException.newException(Unknown Source)
	at org.apache.derby.impl.services.monitor.StorageFactoryService$9.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.derby.impl.services.monitor.StorageFactoryService.createServiceRoot(Unknown Source)
	at org.apache.derby.impl.services.monitor.BaseMonitor.bootService(Unknown Source)
	at org.apache.derby.impl.services.monitor.BaseMonitor.createPersistentService(Unknown Source)
	at org.apache.derby.iapi.services.monitor.Monitor.createPersistentService(Unknown Source)
	... 26 more


```

---

### Post by QBX on 2011-05-20
ok, so the key was the first error:

> java.sql.SQLException: Failed to create database 'jbdb', see the next exception for details.

There was a problem with creating the jbdb database. On checking into the config file in my home directory ~/.jbidwatcher/jbdb, I noticed that all the files were 4 months old - not sure what the problem was as the access rights seemed ok - but either way, I renamed the jbdb directory and now it could create a new jbdb directory from scratch and presto, it logged on and now works beautifully. So I deleted the old jbdb directory and I am hoping to live happily ever after.

Great program!

So there.

---

### Post by momist on 2012-04-17
Just installed JBidwatcher from this HowTo.  Many thanks for the work.

A couple of points:  The current version is 2.5, so the code needs altering from JBidwatcher-2.1.1.jar to JBidwatcher-2.5.jar in a couple of places.

Once the program launches, enter your account name and password and save it, but then when up and running I found it had not been saved to the right place.  Go into "Windows" "Configuration" and re-enter it there to get it to work.  The process is slow (at least it was on my PC) so give it time to file away it's stuff and start up right.

So far so good, my first snipe is scheduled, but I don't know yet if it works.

---

### Post by momist on 2012-05-16
> **momist said:**
> 
So far so good, my first snipe is scheduled, but I don't know yet if it works.

It works very well indeed, I have been running it for a while on Ubuntu 12.04 precise, and have now moved to Lubuntu, where it also works fine.  Many thanks to the developers of this useful software.  :guitar:

Just a note for others, watch the character case used in setting this up.  There are variations on jBidWatcher, jbidwatcher, JBidwatcher.  These easily trip you up.  On Lubuntu, I found that /usr/local/share/applications didn't seem to put the starter on the menu, so I used /usr/share/applications and that worked.  YMMV.

Ian

---

