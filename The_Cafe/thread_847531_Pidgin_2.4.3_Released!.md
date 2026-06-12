---
title: "Pidgin 2.4.3 Released!"
date: 2008-07-02
forum: The Cafe
---

### Post by Kosimo on 2008-07-02
Pidgin folks has just released a fresh new version! 2.4.3

Here the changelog:
> 
	libpurple:
	* Yahoo! Japan now uses UTF-8, matching the behavior of official client and restoring compatibility with the web messenger (Yusuke Odate)
	* Setting your buddy icon once again works for Yahoo! accounts.
	* Fixes in the Yahoo! protocol to prevent a double free, crashes on aliases, and alias functionality
	* Fix crashes in the bonjour protocol
	* Always use UTF-8 for Yahoo! (#5973)
	* Fix a crash when the given jabber id is invalid.
	* Make the IRC "unknown message" debugging messages UTF-8 safe.
	* Fix connecting to ICQ
	* Fix a memleak when handling jabber xforms.

	Pidgin:
	* Include the send button plugin in the win32 build
	* Various memory leak fixes


If you're using Hardy, the easiest thing you can do is download it from [www.getdeb.net](www.getdeb.net)   here: [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

If you want to compile,   as always, download the source code, then:

```
./configure
make
sudo make install 
```

Good luck!

---

### Post by Kosimo on 2008-07-02
By the way, if you download it from getdeb, don't forget to uninstall the current version first!

---

### Post by zmjjmz on 2008-07-02
yeah, I heard that ICQ was blocking connections, is this a fix to that?

---

### Post by Kosimo on 2008-07-02
> **zmjjmz said:**
> yeah, I heard that ICQ was blocking connections, is this a fix to that?

Looks like is fixed. Have a look to the changelog ;)

---

### Post by zmjjmz on 2008-07-02
The question was about it addressing the new problem, or an earlier one.

---

### Post by mech7 on 2008-07-02
I still have this error:

[http://www.nabble.com/-4756:-error-reading-blist.xml-(yahoo.com)-td15235562.html](http://www.nabble.com/-4756:-error-reading-blist.xml-(yahoo.com)-td15235562.html)

:confused:WOuld have thought it would be gone if yahoo uses utf 8 now..

---

### Post by yadayada2 on 2008-07-02
What do you think, how long does it take the new version to enter the ubuntu repositories?

---

### Post by Brainal on 2008-07-02
> **yadayada2 said:**
> What do you think, how long does it take the new version to enter the ubuntu repositories?
I believe it won't. The update will be in the next Ubuntu release.

And on a side note, is there a .deb for amd64?

---

### Post by yadayada2 on 2008-07-02
You think it won't be included within the next days???

---

### Post by Kosimo on 2008-07-02
> **yadayada2 said:**
> What do you think, how long does it take the new version to enter the ubuntu repositories?

It won't be integrated in (Hardy) At least if is not discovered some serious security bug. But it'll be integrated in Intrepid  (probably a newer version than this)

---

### Post by Kosimo on 2008-07-02
> **Brainal said:**
> I believe it won't. The update will be in the next Ubuntu release.

And on a side note, is there a .deb for amd64?

Yes check it out at getdeb, there are 32 and 64 bit .deb's

---

### Post by Brainal on 2008-07-02
> **Kosimo said:**
> Yes check it out at getdeb, there are 32 and 64 bit .deb's

Whoops. I just clicked the download button instead of "Pidgin" then choosing. Thanks

---

### Post by yadayada2 on 2008-07-02
Hmm, doesn't make any sense for me. You see, there are updates coming in nearly every day. So, why should all of the Ubuntu community wait for pidgin until a new major release comes out?

Am I missing some kind of joke?

And when will this Intrepid be released?

---

### Post by Brainal on 2008-07-02
> **yadayada2 said:**
> Hmm, doesn't make any sense for me. You see, there are updates coming in nearly every day. So, why should all of the Ubuntu community wait for pidgin until a new major release comes out?

Am I missing some kind of joke?

And when will this Intrepid be released?
You can either wait or go to getdeb and get them there. Also, Intrepid comes out in fall. You can get an alpha, but it's highly buggy and not really suggested.

---

### Post by Kosimo on 2008-07-02
> **yadayada2 said:**
> Hmm, doesn't make any sense for me. You see, there are updates coming in nearly every day. So, why should all of the Ubuntu community wait for pidgin until a new major release comes out?

Am I missing some kind of joke?

And when will this Intrepid be released?

Because when a new Ubuntu is released, it comes with a specific software version witch has been tested and specifically build for that release.  Then is maintained in order to preserve stability and security issues. But, is "impossible" to update ALWAYS every single peace of software in repos. If you really want the latest one, you have three options. First download, compile and use it. Then if you're too lazy just go to getdeb as suggested. Is free and you're just three clicks away from update your pidgin.  Or wait 'til new Ubuntu version comes with all fresh new FREE repos.

---

### Post by oddsock on 2008-07-02
> **yadayada2 said:**
> Hmm, doesn't make any sense for me. You see, there are updates coming in nearly every day. So, why should all of the Ubuntu community wait for pidgin until a new major release comes out?

Am I missing some kind of joke?

And when will this Intrepid be released?

+1

I don't understand why many updates are coming in for open office, evolution, etc., but Pidgin wouldn't?

---

### Post by yadayada2 on 2008-07-02
I didn't intend to sound ungrateful. Ubuntu rocks. But what about thousands and thousands of new users, who are new to Ubuntu and maybe download it right now. When they come to install their instant messenger application and see how much recommended pidgin is, the first thing they experience is an error message. And that won't be fixed until fall or they have search the internet, find debget and so on?

As I understood it, Ubuntu is just about bringing Linux to the desktop, making it accessible to people with less experience about programming stuff. :confused:

---

### Post by Kosimo on 2008-07-02
> **yadayada2 said:**
> I didn't intend to sound ungrateful. Ubuntu rocks. But what about thousands and thousands of new users, who are new to Ubuntu and maybe download it right now. When they come to install their instant messenger application and see how much recommended pidgin is, the first thing they experience is an error message. And that won't be fixed until fall or they have search the internet, find debget and so on?

As I understood it, Ubuntu is just about bringing Linux to the desktop, making it accessible to people with less experience about programming stuff. :confused:

I didn't feel you ungrateful ;)  No probs.
If you're new to the community. First of all: Welcome :)  
Then, as said if you want to upgrade your pidgin there is a very very easy way to do it. Go here: [http://www.getdeb.net/release/2883](http://www.getdeb.net/release/2883)  download this three debs.  

Then open the Terminal:  Applications > Accessories > Terminal

and type:  sudo apt-get remove pidgin  (It'll ask for your password)

After this, install those three downloaded debs in this order:

1st. pidgin-data
2nd. libpurple0
3rd. pidgin

Just need to double click to each deb.

Hope it helps.

And about the update, as I said, now ubuntu devs are really busy creating, testing and compiling Intrepid Ibex. And no peace of software in Hardy will be upgraded (as said, only if it doesn't have a serious bug or security hole)

---

### Post by LinuX-M@n1@k on 2008-07-02
> **yadayada2 said:**
> i Didn't Intend To Sound Ungrateful. Ubuntu Rocks. But What About Thousands And Thousands Of New Users, Who Are New To Ubuntu And Maybe Download It Right Now. When They Come To Install Their Instant Messenger Application And See How Much Recommended Pidgin Is, The First Thing They Experience Is An Error Message. And That Won't Be Fixed Until Fall Or They Have Search The Internet, Find Debget And So On?

As I Understood It, Ubuntu Is Just About Bringing Linux To The Desktop, Making It Accessible To People With Less Experience About Programming Stuff. :confused:

+1 ;)

---

### Post by LookTJ on 2008-07-02
I was wondering why it was randomly crashing. Well there's my answer, it was a certain "memleak" :)

---

### Post by Extreme Coder on 2008-07-02
The fact that no new major updates for applications are added is one of the main reasons I have moved to Mandriva..
Anyway, I still won't use Pidgin, especially since they don't support A/V, and apparently the devs don't want to.

---

### Post by Kosimo on 2008-07-02
> **Extreme Coder said:**
> The fact that no new major updates for applications are added is one of the main reasons I have moved to Mandriva..
Anyway, I still won't use Pidgin, especially since they don't support A/V, and apparently the devs don't want to.

Audio and Video is scheduled to be included this year (Maybe after googlecode?) 

Have a look to pidgin's roadmap (temporally down)
[http://developer.pidgin.im/roadmap](http://developer.pidgin.im/roadmap)

---

### Post by Mr. Picklesworth on 2008-07-02
It should be clarified: There is a chance that an update like this will find its way back in Hardy via the Backports. (System -> Administration -> Software Sources).
For example, Wine tends to be kept up to date in this way. Components like Pidgin, where upgrading is not exactly important, don't always get the same treatment... but it's possible.

---

### Post by mustang on 2008-07-02
Thanks for posting the getdeb link. Installation went smoothly.

---

### Post by Polygon on 2008-07-03
if ubuntu updated every single piece of software that got updated, ubuntu would be a lot more buggy. they have a repo freeze during the development cycle for a reason, so people can test the certain combination of software and iron out most of the bugs and then release it. If every single program was updated when it got updated, then stability issues might crop up.

and like its been said countless times, if the repo version is too outdated or you NEED the latest version for some reason, it is trivially easy to install from getdeb.

---

### Post by LookTJ on 2008-07-03
> **Polygon said:**
> if ubuntu updated every single piece of software that got updated, ubuntu would be a lot more buggy..I would disagree with this statement 98% of the time. But I won't say no more since I will be a gentleman and not argue. :)

---

### Post by kevdog on 2008-07-03
Forget getdeb -- compile from source -- it takes about 10-20 mins.  Its actually easy to do, and you can customize.  I don't know why people are scared of compiling? Its easy, you learn something, and you get the program the way you want it.

---

### Post by elfstone2 on 2008-07-03
> **Kosimo said:**
> 
And about the update, as I said, now ubuntu devs are really busy creating, testing and compiling Intrepid Ibex. And no peace of software in Hardy will be upgraded (as said, only if it doesn't have a serious bug or security hole)


Uhm... can you please explain, what you mean with "a serious bug"?
Pidgin is rendered completly useless for maybe 30% - 70% of its users. (Don't know how many people use icq instead of other IMs, in this part of the world its more like 80%).

Its not a small bug, some new feature or some convenient change. The program is completly disfunctional. Its like you cant open or save documents with Openoffice.

If this bug is not fixed _very_ soon in the repos, ubuntu loses a hell of a lot of its credibility to be userfriendly.

(And yes, helping me and others here to update it with .deb is very nice, and im not too lazy (my other PC runs gentoo), but ubuntus philosophy is to be easy - not to compile things from source or manually download a deb-file).

---

### Post by toupeiro on 2008-07-03
> **kevdog said:**
> Forget getdeb -- compile from source -- it takes about 10-20 mins.  Its actually easy to do, and you can customize.  I don't know why people are scared of compiling? Its easy, you learn something, and you get the program the way you want it.

I dont think its always a matter of fear than it is a matter of convenience.  Whose to say the deb won't give me the program exactly the way I want it?  And if it doesn't guess what option 2 is? :-D

---

### Post by mrgnash on 2008-07-03
> **kevdog said:**
> Forget getdeb -- compile from source -- it takes about 10-20 mins.  Its actually easy to do, and you can customize.  I don't know why people are scared of compiling? Its easy, you learn something, and you get the program the way you want it.

I compiled Pidgin 2.4.3 from source, and it didn't fix the ICQ problem -- I suppose because it was going over the top of the old libpurple or something.

---

### Post by change_mode on 2008-07-03
Yea, this should get an update from the official repo. I understand that the devs are busy, but without the update Pidgin can just be removed completely, because it's useless.
The great thing about Ubuntu so far I thought is that I get all the updates I need to run my system automatically. And I need ICQ. :)

By the way, when I install the .deb, will Pidgin show up in the Synaptic Package Manager and the Add/Remove application?

---

### Post by mech7 on 2008-07-03
> **change_mode said:**
> By the way, when I install the .deb, will Pidgin show up in the Synaptic Package Manager and the Add/Remove application?

With me only in synaptic.. which is kinda not user friendly to uninstall :(

---

### Post by alkemyst on 2008-07-03
I think also that this is to be treated like a major bug.
A patched version (still named 2.4.1, but working with icq) is now available in the "proposed" repositories.

Go to
System->Administration->Software Sources
and enable
"Proposed" under "Updates"

You should get a message asking to reload the software repositories. Say yes, and then you should immediately see the "updates available" icon. The only packages you need to update are those called "pidgin..." and "libpurple..."

---

### Post by sefs on 2008-07-03
Compiling would be nice if somehow the resultant installation can be managed by the package manager in use.  But by compiling and installing from my recollection you end up with a whole lot of stuff that you cannot track what is installed on your system no?

> **kevdog said:**
> Forget getdeb -- compile from source -- it takes about 10-20 mins.  Its actually easy to do, and you can customize.  I don't know why people are scared of compiling? Its easy, you learn something, and you get the program the way you want it.

---

### Post by zachtib on 2008-07-03
> **sefs said:**
> Compiling would be nice if somehow the resultant installation can be managed by the package manager in use.  But by compiling and installing from my recollection you end up with a whole lot of stuff that you cannot track what is installed on your system no?

prevu...

apt-get source it, preferably from intrepid, or dget -x the .dsc file from packages.ubuntu.com

then run prevu, it'll build a deb and maintain a local apt repository of all your cusomt compiled packages.

---

### Post by Monolith on 2008-07-03
**edit*

Never mind. I'm a moron. Move along folks, there's nothing to see here.

---

### Post by OZFive on 2008-07-03
I am still having an issue with Pidgin and Guifications on the XMPP Service.  Getting 4 of the pop ups for each action on that service.  Annoying as it does not happen with other services.

---

