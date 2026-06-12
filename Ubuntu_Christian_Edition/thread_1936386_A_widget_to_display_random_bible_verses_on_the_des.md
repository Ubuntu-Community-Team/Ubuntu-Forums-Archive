---
title: "A widget to display random bible verses on the desktop?"
date: 2012-03-06
forum: Ubuntu Christian Edition
---

### Post by nullified_nostalgia on 2012-03-06
Does anyone know of a widget to display different random bible verses on the desktop at a user selected interval?  I've done a lot of searching on the web for something like this and there's a lot of them for windows but I'm having trouble finding one for linux.

Any help in finding something like this would be greatly appreciated.  Thanks!

---

### Post by Dry Lips on 2012-03-06
There is something called bibleVerse for KDE. I don't think it's in the repos, so you'll have to download it or build it from source.

[http://kde-apps.org/content/show.php/bibleVerse?content=108668](http://kde-apps.org/content/show.php/bibleVerse?content=108668)

---

### Post by jonathonblake on 2012-03-07
> **nullified_nostalgia said:**
> Does anyone know of a widget to display different random bible verses on the desktop at a user selected interval?  

gVerse, for Gnome desktops. You will have to compile it.

jonathon

---

### Post by nixblog on 2012-03-07
> **nullified_nostalgia said:**
> Does anyone know of a widget to display different random bible verses on the desktop at a user selected interval?  I've done a lot of searching on the web for something like this and there's a lot of them for windows but I'm having trouble finding one for linux.

I just use a script to pull down BibleGateways verse of the day and get Conky to display it on the desktop

You can see an example over at [Christian Forums]("http://www.christianforums.com/t7570314/")

---

### Post by garyzw on 2012-05-22
I like this idea-- would you please give step by step instructions on how to get BibleGateways verse of the day to do this?


> **nixblog said:**
> I just use a script to pull down BibleGateways verse of the day and get Conky to display it on the desktop

You can see an example over at [Christian Forums]("http://www.christianforums.com/t7570314/")

---

### Post by prism01 on 2012-11-26
This is an old thread but this author mused that a comment about Conky might be in order.

If one was to present Conky to an imaginative teenager, given that DansGuardian would not allow access to suspect internet sites, the Conky script would provide to the teenager a really cool way to customize the desktop so that the person could say to her or his friends..."hey...I did that!"


And....it would occupy the mind of a child for a while so as the Devil would not find a workshop....however there is the alternate view that letting the child onto the net at all is exposing he or she to the Devil's work so...one will have to make a decision about the child...

But...children learn best at mother's (grandmother's) knee....so possibly a parent might get some good interaction time in with the child in the process! :)

And the child would also learn something about "coding", leading, possibly, to a lucrative job in making websites for.....churchs! :)

a) Conky is a way to display system information on the desktop.  
b) it is extremely customizable and there are a myriad of ways to do it on the net, however, most of them would involve backgrounds on the desktops that were of an unacceptable nature to most Christians.
c) However, that, in and of itself, presents a challenge.  If a Christian user made a Christian themed desktop and then placed Conky on it that would be a ...cool thing.
d) Conky is a "hidden" script.  There are distros which are precisely arranged to display Conky, however the Gnome desktop is not so specifically arranged.
e) The really cool thing about Conky is when one has "transparency" involved so that one does not see a background behind the text of the display, as in the colour of the background behind what one is reading in this very post.
f) However, Gnome conky is not easily made to do "transparency".  In most cases the transparency is not transparency at all, it is a second rendering of the background and really is rather an illusion.
g) If one was, indeed to get the conky script running there would be a default black background, that does not "flicker" so that is a good thing.
h) The background colour can be easily changed in the script to any of the colours for the net such as:

[http://html-color-codes.com/](http://html-color-codes.com/)

one merely replaces the html: 000,000 for black to the desired colour.

i) then the challenge would be to be very discerning in choosing a background which had a colour which would blend/contrast with/compliment the chosen colour.

if anyone has particular questions about Conky, this author has some experience with it in KDE but not Gnome, but this author would be glad to help as can be.

However, there are many, many, many more people at the Ubuntu forums which have a lot more information concerning the Gnomish way of doing the Gnomish way of doing things, or the Unity(ish) way... lol

prism01

---

### Post by prism01 on 2012-11-26
Please read this author's previous post concerning using Conky to display "random bible verses" and the prior post concerning the particular script for said Conky display.

The point of this post: how to get Gnome to run a "Bible verse" natively.

Since this author is unfamiliar with the "install history" of the people who are running UbuntuCE this post will be, a-purpose, rather general.

There might be several options for displaying "random Bible verses" on the desktop.

a) a "gdesklet"
b) an RSS feed

a) a "gdesklet" is an application that will display certain things on the Gnome Desktop.
b) Unity may, or may not, run gdesklets, depending upon the user's particular install.

Perforce, as stated above, this post is generalized.

The below sections will deal with gdesklets and RSS feeds.

c) gdesklets is in the repositories and one can download them.  Again, depending upon the users install there are different gdesklets.

d) gdesklets can also be installed from a "tarball" but that might be beyond the casual( to Linux) users of UbuntuCE.

If anyone wishes to have particular information about installing "a tarball" there are many posts on the net or this author might provide some small assistance.

It is basically "unzipping" a package but it has to be done from "terminal" as opposed to the MS way of paying to have an application to "unzip".

Be that as it may, there are several gdesklets which may serve the purpose such as: Bible Time and  PrayerTime

Here is a list of the tarballs available, which may, OR MAY NOT, install upon one's system:

[http://www.gdesklets.info/archive/](http://www.gdesklets.info/archive/)

RSS FEEDS:

An RSS feeder is a very simple way to get "breaking news" or any other kind of information onto the desktop.

Here is an example of one called: Newsgrab

[http://www.gdesklets.de/?q=desklet/view/61](http://www.gdesklets.de/?q=desklet/view/61)

And here is a representation of how it would appear on the desktop:

[IMG]http://www.gdesklets.de/files/desklets/NewsGrab/NewsGrab-1.5.png[/IMG]

There are several "feeders" of Bible verses, prayers, etc available and one need merely copy and paste an URL into the application to display the feed.

Here is a listing of some URLs which will display Bible verses in such an application as that one referred to above:

[http://abibleverse.org/rss.htm](http://abibleverse.org/rss.htm)

if anyone has questions, this author will attempt to help, but the folks at Ubu forums or the moderators might better be able to so do.

prism01

---

### Post by nixblog on 2012-12-03
> **garyzw said:**
> I like this idea-- would you please give step by step instructions on how to get BibleGateways verse of the day to do this?

Many apologies, I totally missed your post asking for a how to on this until the thread was revived a few days ago. 

If anyone wants that conky script to show the bible verse on the desktop then I will fire up UCE and get a working version for anyone that needs it -just ask :)

---

### Post by prism01 on 2012-12-04
Hi nixblog

That is a very nice offer! :)

Surely at least a few would like to try it!

The problem for most folks, including this author, is that of transparency.

The Unity interface might cause a big problem with flicker and the double scanning might be a good idea, just a thought.

Most folks seem to get being able to change the colour of the background but the transparency is what a lot of folks find to be tres kewl!

And, it might be assumed that newer YOUNG folks would like to see an example of your conky script.

However, with the holidays coming up, maybe not a huge rush, after all, family and friends along with the Guy Up There come first! :)

woodsmoke

---

### Post by nixblog on 2012-12-10
Right then, here's the howto based off some notes I wrote for getting this to work and it should (hopefully) work for you too.

This script displays text from biblegateways verse of the day on your desktop. it also works best with "non-busy" backgrounds for ease of reading. It has been tested on a vanilla 12.04.1 install in Virtualbox and works fine.

bgverse needs conky to operate so you will need to install conky,

    ```
sudo apt-get install conky
```Create hidden directory in your home directory called ".bgverse", 

    ```
mkdir ~/.bgverse
```Download bgverse.tar.gz (see attachments) and extract files to hidden directory .bgverse (which you created in the step above),

   ```
 tar -xvf bgverse.tar.gz -C ~/.bgverse
```This will unzip two files into ~/.bgverse - these are,

    **bgverse** (main script, downloads and extracts verse from html code then runs conky)
    **conky_todaysverse.conf** (conky script to display verse on desktop)

Make sure the file bgverse has execute permissions - if not then,

   ```
chmod a+x ~/.bgverse/bgverse
```All being well you can test it by issuing the following command,

    ```
~/.bgverse/bgverse
```There will be bit of a delay delay (so be patient) before anything shows up as this gives time for slower machines to start the Unity desktop before launching conky during login.

This will be needed to be run manually everytime you login unless we automate it, so...

Open "Startup Applications" utility via Unity Dash search and create a new startup entry with the following details for example,

**Name: **bgverse
**Command:** /home/<your homedir>/.bgverse/bgverse  (you can browse to the bgverse script)
**Comment: **Display BibleGateway verse on desktop

Once saved (haha no pun intended) it should launch automatically at login!

Enjoy :)

The bgverse script is pretty well commented so I guess I shouldn't need to explain how it works. The text colors can be changed in the conky config script by using the appropriate RGB color codes for the "default_color c47434" line which is the master text color, used for the header in this case. Also, on the last line, we have "${color bf8f3f}" which is the text color control code for the verse itself.

I have also tested this on my six year old Lenovo laptop and it works perfectly!

---

### Post by prism01 on 2012-12-11
That is a great Conky script nixblog! :P 

As to an RSS feeder.

There are many, and here is a discussion for Gnome:

[http://gnomejournal.org/article/25/rss-feed-readers-for-gnome](http://gnomejournal.org/article/25/rss-feed-readers-for-gnome)

A good one for KDE and it's iterations is "RSSnow".

All of the feeders should be in the repositories for whatever desktop one is running.

In most cases one can either "drag" the symbol for the url of the feed, in the long URL box, not the search box, into the feeder.

Or there is a menu system for one to copy and paste the url.

Here is the discussion page of what an RSS feed is and a linky for the  RSS feed at BibleGateway, the link to the RSS feeder is part way down.

[http://www.biblegateway.com/info/rss.php](http://www.biblegateway.com/info/rss.php)

If you want to skip the discussion and go to the feed page, here it is.

[http://www.biblegateway.com/votd/get/?format=atom](http://www.biblegateway.com/votd/get/?format=atom)

prism01

---

### Post by nixblog on 2012-12-11
> **prism01 said:**
> That is a great Conky script nixblog! :P 

As to an RSS feeder...

Thanks, I guess the conky script will be of use to some people :)

For RSS, I tend to use Liferea but you could use the RSS capability built into Thunderbirds email client. If you are a cloudy sort of person then Google Reader could be of use and you can use that from anywhere as it's web based.

---

### Post by parkernathan on 2013-05-16
Check out Verse of the Day on Biblia.com from Logos. They're doing high-res images of Bible verses for Windows 8 and could probably give you the API's for Ubuntu.

---

