---
title: "What OS for my 90 years old grandma?"
date: 2008-11-22
forum: The Cafe
---

### Post by torbengb on 2008-11-22
Can you help me find a Linux variant that is useful to my 90 year old grandmother? 

What I'm looking must be so simple that there is nothing that the can be afraid of breaking. No user profiles, no login, no right-clicking, not even a desktop or filesystem. The only thing it must be able to do is send/receive email, view photo attachments, browse the web, and have an address book. 

Many years ago I saw some simple desktop OS'es that were rather like a Psion PDA or perhaps like today's Asus Eee. Sadly, I can't recall the names of those systems. I have been trying to find such super-easy systems again but apparently nothing of the kind exists anymore. Today there are so many Linux variants but they are all fully-featured systems, and though that's all really great for the average geek like me, it's not dead-simple anymore, if it ever were.

--> Can you point me to a Linux system that is truly easy and simple?

-- 
Torben G-B

---

### Post by theApokalypsis on 2008-11-22
you should check out the netbook remixes of some linux OS's. They are really restricted OS's that are primarily used for email/messaging etc. 

[http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)
I know Ubuntu has one as well as some others. 
Like LinPus (sp) that came with my Acer Aspire One (which i removed btw).

---

### Post by kerry_s on 2008-11-22
any linux will do, YOU just have to customize it.
make the fonts bigger, stretch the icons, use a single panel if there's 2, only put the basics on the panel(taskbar,clock) everything needed should be reasonable size icons on the desktop.

as long as you take into account her needs, you should be able to make it very simple.
for example:
my grandma(she's 86) has shacky hands, thus large icons, her vision is still pretty good she was happy with 14 size fonts.

i used the standard gnome, it was easy to drag and drop the programs she wanted to use right from the menu on the desktop, then right click on them> resize.

it took all of 30min to setup the desktop, but i spent an hour or so making sure the right programs were there before i sat down with her, the media codecs needed, acrobat instead of evince and so on.

i used debian lenny, upgrades are more dependable and i won't ever have to install again.
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by philinux on 2008-11-22
What are the specs of the pc she'll be using?

---

### Post by ugm6hr on 2008-11-22
A custom installation may be appropriate.

Just create a user without admin privileges for her.

You could remove the menu completely, and just have a single (large) panel with shortcuts to the apps she needs, in addition to a single Log Off button.

Don't forget to remove the second desktop too.

---

### Post by TeXtonyx on 2008-11-22
You can change only some of the controls for fonts with Preferences for different areas. 
Here is my userChrome.css (between dotted lines, which you could cut&paste. 
You can create the file which sudo gedit. Also create the chrome directory if needed. 

----------------------------------

{

font-size: 20pt !important; 
 

}

window {
  font-size: 5.5mm !important;
  font-family: Adobe Caslon Pro Bold !important;
}

ac-comment {font-size: 200% !important; color: #444444 !important; }

.ac-comment[selected='true'] { color: #FFFFFF !important; }

.ac-url-text {font-size: 200% !important; color: #000077 !important; }

.ac-url-text[selected='true'] { color: #FFFFFF !important; }

menubar, menubutton, menulist, menu, menuitem {
  font-family: helvetica !important;
  font-style: italic !important;
  font-weight: bold !important;
  font-size: 4mm !important;
}

--------------------------------------------

You can increase or decrease where is says font size xxpt and also 
where is says font-size, xmm, change 4mm to 5.5mm or 5mm for instance.

This works for Firefox and/or Thunderbird, Linux or Windows->different folder. 

/home/username/.mozilla/firefox/xxxxxxxx.default/chrome/userChrome.css

/home/username/.mozilla-thunderbird/xxxxxxxx.default/chrome/userChrome.css

C:\Documents and Settings\UserName\Application 
Data\Thunderbird\Profiles\xxzrc98n.default\chrome\userChrome.css

C:\Documents and Settings\Username\Application 
Data\Mozilla\Firefox\Profiles\xxzfc6gj.default\chrome\userChrome.css


To see dot files, . , you need ls -la from the command line or 
turn on 'Show hidden files' which is under View in the file browser.

This is besides the customizing one can do in Preferences, and I 
think the most important setting to change is 'minimum font size' 
and uncheck 'allow webpages to choose their own fontsizes' if 
you want to make sure the fonts are always large enough to see.

Also NoSquint, [http://urandom.ca/nosquint/](http://urandom.ca/nosquint/) it's a Firefox plug-in
which will allow automatically magnifying everything at all sites
which is good at 125% for many visually impaired.

---

### Post by Swagman on 2008-11-22
Auto login

AWN with just mail, firefox & shutdown

---

### Post by kernelhaxor on 2008-11-22
I would recommend windows XP

EDIT: Scratch that.  I just read that you are only looking for a Linux variant.  The thread title jus said 'What OS' , so I said it.

---

### Post by billgoldberg on 2008-11-22
Install Ubuntu.

Make sure there is only one panel.

Make desktop shortcuts to firefox, the home folder, ...

Make sure the resolutions isn't set to high.

Set the fonts up to something bigger.

Make sure it auto-logins.

Make sure the updates are automatically downloaded and installed.

And make sure you show her how to open and use firefox and some other programs.

---

### Post by jimi_hendrix on 2008-11-22
dont forget to tell her to call you if she has a problem :)

and write down basic step by step instructions and put it on a notepad next to the computer for her

---

### Post by Old_Grey_Wolf on 2008-11-22
Has your grandmother used a computer before? If so, what OS?

Would anyone other than her have access to the computer? The Internet connection could get abused.

---

### Post by torbengb on 2008-11-25
Thank you all very much for your responses! Let me answer the important questions:

[LIST=1]
[*]She has never used a computer before. The VCR is the most advanced thing she has ever owned and used (but that without any problems). 
[*]The computer will be some kind of standard modern laptop and a USB mouse.
[*]The computer will use wireless LAN to some kind of always-on home DSL connection or similar.
[*]No one else will use or have physical access to the computer. The nearest family member is 2 hours away and isn't me, so onsite support should be avoided. Theoretically, support over the Net should be possible, but the idea was to make it not necessary. "Nothing to break" is the goal.[/LIST]
@kerry_s:
I have no Linux experience at all, so customizing a system myself may not be achievable. I can't even make my Ubuntu system see another local Windows computer's network shares. ("Awn" looks good! If only the apps themselves weren't still regular full-featured apps and not dead-simple can't-break deals.)

@kernelhaxor:
I have significant Windows experience (3.0 ~ Vista) and don't believe that any Windows version will be solid enough for this purpose.

Perhaps some forum member will be able to recall some super-simple variant that would be useful. I am still listening to your comments! Thank you very much.

---

### Post by Sef on 2008-11-25
What applications will she be using?

---

### Post by sydbat on 2008-11-25
I installed the basic Ubuntu 8.04 32bit on my 81 year old father's computer at his request. I set everything so it won't break and have the desktop fonts set high and increased the desktop icons he wanted to be larger (he is nearly blind). When he has any problems (which WILL happen no matter what) I simply remote in...we are about 1000 km apart...a quick phone call to access the desktop.

I think your Grandmother will have no problems to speak of, as long as she is willing to learn (sounds like she is) and knows she can call you for problem solving when things happen (not often with Ubuntu as a basic email/surfing/document writing machine).

Also, let her know how proud you are of her for learning this kind of thing. I tell my dad (and everyone else) how cool it is that he chose to learn a new OS at his age...and that he finds it better (in lots of ways) than XP. If he can do it, anyone can.

---

### Post by Paqman on 2008-11-25
> **kernelhaxor said:**
> I would recommend windows XP


I wouldn't. Too much maintenance required to keep it running well. Definitely a job for Linux. Customised desktop environment, LTS release with automatic security updates, install and forget.

---

### Post by kerry_s on 2008-11-25
> @kerry_s:
I have no Linux experience at all, so customizing a system myself may not be achievable. I can't even make my Ubuntu system see another local Windows computer's network shares. ("Awn" looks good! If only the apps themselves weren't still regular full-featured apps and not dead-simple can't-break deals.)


it's not rocket science, i'm just saying make it look simple.
the only skills you'll need is drag & drop, the mouse right click.
try it, open your application menu, left click and hold while moving to the desktop, now right click it and resize. it doesn't take a genius to move things around so the stuff needed is right there and she doesn't have to deal with menus.

does she need to browse network shares?

---

### Post by torbengb on 2008-11-25
I expect she will only need to send/receive email, view photo attachments, browse the web, and have an address book (for the mail addresses).

I can't even imagine that she would ever be likely to save an attachment locally, or do anything even savvier than that. So we're talking REALLY basic usage here.

---

### Post by chucky chuckaluck on 2008-11-25
> **torbengb said:**
> I expect she will only need to send/receive email, view photo attachments, browse the web, and have an address book (for the mail addresses).

I can't even imagine that she would ever be likely to save an attachment locally, or do anything even savvier than that. So we're talking REALLY basic usage here.

gmail would be perfect for her. it has an address book, plenty of storage and you can easily view pics and just save the emails. it's pretty easy to use and you could access her account from anywhere if you needed to help her with something.

any simple distro would work. set her up with a one workspace openbox with something like fbpanel that has icons for the few apps she'll need. use gdm setup to automatically log her in. if you use a rolling release distro like arch, you'd never have to reinstall, just update it.

---

### Post by halovivek on 2008-11-25
install ubuntu and make the fonts and other things to view bigger. dont forget to do one more thing just give her only one work station.

---

### Post by lifestream on 2008-11-25
Well, there isn't a OS out there called "90 year old Grandma Operating System", so you'll have to do the things suggested here yourself.m

Fonts : Go to  System->Preferences->Apearance, then to the Fonts tab.
First of, pick simple and readable fonts. Then make them bigger. You'll see how easy it is to do.
Then: Click Details on that Font tab. Where it says "Resolution", put 100 or above.

Make shorcuts on the desktop. Firefox/Epiphany, Evolution (or Gmail, or whatever she uses. For an older person I think web mail is easier, because it's dead simple, and there's no right click). If it's say, Gmail, put a web shortcut on her desktop. 
Etc etc etc. 
Then: Right click each icon, select Stretch. Drag the borders so the icon is 2 inches tall.

Make  her background a dark color. It's easier on the eyes.
Make her theme something with good contrast. The "Contrast theme on ubuntu is a joke.

Look at the theme. Is it easy to say which tab, which window, is the active one?
Is the window backgrounds too bright? 

Tell her about the mouse scrool, so she is not fetching for those sidebar up/down arrows :3

Go to System>Preferences>Software Sources
Enable automatic download and install of updates.
If she has slow connection, you might want to disable updates completely.

Does she get distracted or frustrated easy? You might want to install Firefox Adblocker and G filterset updater, available from Firefox Add Ons website.
Also,[ Mike's hosts file]("http://everythingisnt.com/hosts.html")


And bonus points and kisses from her: make a dekstop folder called Photo Albun, and put photos she likes in there! Make that folder show big image previews :)

Go and try to do this. If you run into any problems, post here!

---

### Post by Old_Grey_Wolf on 2008-11-25
Take a look at gOS at [http://www.thinkgos.com/gos.php](http://www.thinkgos.com/gos.php). There are a lot of people that don't like it but it is simple and easy to use. Also, it is based on Ubuntu and has access to the Ubuntu repositories.

---

### Post by torbengb on 2008-11-26
Many many thanks to all of your comments. This is really helping me forward, and you have many good suggestions! And special thanks @lifestream for the excellent summary and to old_gray_wolf for the gOS link -- that looks about right!

Now I am going to set up a test system and try out your ideas. Thank you again so very much for the help, and please continue posting if you have further comments.

---

### Post by Old_Grey_Wolf on 2008-11-27
I was looking through some distros I have set up as Virtual Machines and saw Puppy Linux. You may be interested in it as well. Homepage: [http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by MenZa on 2008-11-27
Check out [this link](http://tombuntu.com/index.php/2007/08/17/making-my-grandparents-leet-linux-users-part-1/). You could just expand on the ideas to make it even simpler. :)

---

### Post by bwallum on 2008-11-30
I've done a couple of machines for elderly folk now. A big screen and large fonts are at the top of the list I'd say. The OS I used was Ubuntu. If you want to play safe use Hardy or Intrepid (that's what I used). You can set up their username and password to be their first name, it gets shown in the top panel and then whenever they need to confirm updates the authentication name is there for them without them having to remember. Really good for me when servicing the machines as well.

I also put start up icons on the top panel for browser, mail (already there by default) and other programs such as text editor, vlc player (for dvds), terminal (yes they can use them when guided over the phone) photo manager and my own text file giving them my email address and telephone number really simply for them to get at if confused. In the browser make sure you have links to their favourite news source, iplayer or similar (I'm in the UK) and Ubuntu forum.

I never restrict any functionality and was totally surprised when one gentleman showed me a panoramic picture he had made using hugin and his own scanned pictures! I never underestimate what somebody can do with enough patience and interest. 

Beware the grandkids stealing it though.

---

### Post by torbengb on 2008-12-02
> **bwallum said:**
> whenever they need to confirm updates the authentication name is there for them without them having to remember.I hope there's a way to stop any such notifications. It's good that you have great experiences with senior users but I still don't want my granny to see such "techie stuff". I don't even know what it is myself!

> **bwallum said:**
> Beware the grandkids stealing it though.Er... that would be me.

---

### Post by DeadSuperHero on 2008-12-02
Just go get your grandmother ENIAC. It makes for a great calculator.

Old computers for old people.

---

### Post by Kvark on 2008-12-02
It doesn't get any easier than [Splashtop]("http://www.splashtop.com/"). ;)

---

### Post by bwallum on 2008-12-02
You can auto install security updates. 

System>Administration>Software Sources, then use the update tab to set up (click on a radio button).

I wouldn't spoil the fun by being too constrictive though.

---

### Post by tgalati4 on 2008-12-02
We're getting a Jitterbug phone for Grandma.  Perhaps someone should spin a Jitterboog distro with similar theme--big numbers and limited functionality.

---

### Post by Bölvaður on 2008-12-02
> **bwallum said:**
> You can auto install security updates.

You should actually restrict some updates, like kernel and manually install the missing updates your self every other year.
Updates are able to break your system and that is to avoid by all means.


I really like some posts here, but some updates are no no.[-X[-X

---

### Post by linuxguymarshall on 2008-12-02
> **torbengb said:**
> 
What I'm looking must be so simple that there is nothing that the can be afraid of breaking. No user profiles, no login, no right-clicking, not even a desktop or filesystem. The only thing it must be able to do is send/receive email, view photo attachments, browse the web, and have an address book. 


A Mac Mini with OS X or if you wan't Linux get her the  [Everex&#8217;s TC2502 gPC]("http://www.walmart.com/catalog/product.do?product_id=7754614").

I know I suggested computers, not Operating Systems. But the Mac Mini is a good way to get OS X and the gOS came on that computer and it's cheap. Never a bad time for a hardware upgrade

---

### Post by magnus0 on 2008-12-02
Just put the launchers of programs she needs on the desktop and resize them very big. And you could even use Screenlets to put a digital clock on the desktop or something..

---

