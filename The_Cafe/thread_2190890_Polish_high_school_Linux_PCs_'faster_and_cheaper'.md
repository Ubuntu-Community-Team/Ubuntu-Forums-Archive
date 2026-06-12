---
title: "Polish high school: Linux PCs 'faster and cheaper'"
date: 2013-11-29
forum: The Cafe
---

### Post by henke54 on 2013-11-29
> The Zolnierzy Sybiru high school in the Polish city of Lubawka says that switching school PCs to Linux has made them faster, while saving money otherwise spent on licences for proprietary software, reports FWIOO, the foundation for Free and Open Source Software. The school has converted 11 of its PCs to running Ubuntu Linux, shared by 55 students. The switch is the initiative of one of the school's teachers.
[https://joinup.ec.europa.eu/community/osor/news/polish-high-school-linux-pcs-faster-and-cheaper](https://joinup.ec.europa.eu/community/osor/news/polish-high-school-linux-pcs-faster-and-cheaper)
:popcorn:

---

### Post by Linuxratty on 2013-11-30
Soon this will spread. I'm looking forward to it.

---

### Post by The Cog on 2013-11-30
Sadly, it's still a rare enough event that it's still newsworthy. 
Think how much better off the world's education system would be if they all used Linux. Not only would they save a fortune, they would be able to teach proper computing instead of just teaching secretarial skills on applications that the vendor will make obsolete before the students actually land secretarial jobs.

---

### Post by turgenjev1 on 2013-12-01
Poland is the sixt biggest economy in Europe, so these are great news.

---

### Post by Old_Grey_Wolf on 2013-12-01
> **The Cog said:**
> Sadly, it's still a rare enough event that it's still newsworthy. 
Think how much better off the world's education system would be if they all used Linux. Not only would they save a fortune, they would be able to teach proper computing instead of just teaching secretarial skills on applications that the vendor will make obsolete before the students actually land secretarial jobs.

Sadly, Microsoft Windows system admins are easy to find and cheep. When I retired 7 months ago, I was making a very good living because of my Linux knowledge.  I think the schools may be concerned that they can't afford the people that know enough to support a Linux system. They listen to what the sales person is telling them about the cost of training, etc.

As far as teaching proper computing, I have my doubts. They may just switch from teaching Microsoft Office and Photoshop to teaching LibreOffice and GIMP. 

:)

---

### Post by Roasted on 2013-12-02
For what it's worth, we've been implementing something similar right here in Pennsylvania, USA, with our school district I work at. Two years ago we implemented Ubuntu on some netbook-esque machines running some of the earlier AMD APUs. They weren't Atom systems and had a bit more power, but they admittedly are not going to break any speed records in the encoding department, but it's been nice to run Ubuntu 12.04.3 on them and to see them continually chug along with extremely low maintenance. We use Puppet as our management system and have our own internal git repo set up so we can push changes to them accordingly. As an example, we have a star menu on our taskbar with links directly to common educational resources. I just pushed a new link to a few hundred machines via git/puppet/etc which auto added the bookmark accordingly. It was crazy easy.

In the days of our initial Ubuntu considerations two years ago, we were on the fence in several areas about which desktop environment to run. Unity was a mess, Gnome was just lifting off, and KDE felt a little meh overall. I've heard of some districts launching a locked down KDE (so there wasn't a gazillion tweaks to mess with) with success, but in our eyes, XFCE just made more sense. XFCE was heavily customized, so we have our own little Windows 7/Mac OSX-esque layout which is familiar for anybody to pick up. We've tinkered with the thought of implementing another environment, but it was all but a 2 minute conversation to cross Unity off the list for various reasons, and Gnome Shell (which I and several others in the department love) is too wildly different to really venture down that training road just yet. Especially when you consider the ease of use of XFCE with our setup, it's a difficult toss up to side with changing the environment when the current one works, and works dang well. 

Traditionally we've been a Mac shop, but with Apple killing off the white Macbook (which was up there in price for us but still tolerable), it left us with the Macbook Pro and Air as viable alternatives. Apple of course is quick to offer up the iPad as a lower cost solution, but c'mon. You can put any keyboard on any tablet and think it's a laptop replacement, but there are countless road blocks in existence that stomp that stance almost immediately. That's where the turn came about to invest some energy looking elsewhere. Given the fact that Linux overall (not just Ubuntu) has grown so, so very much in recent times, it's truly evolved into an actual replacement operating system versus the Windows and Mac alternatives. I couldn't say this with 100% confidence even 5 years ago, despite my intense support and interest in Linux then. Bu now... I can.

My boss has done several presentations regarding this major transition, namely at the Central PA Open Source Conference, which highlights some of the good/bad/ugly that we experienced with the transition. Switching platforms isn't easy, and it takes some infrastructure changes as well as training for end users. Considering the magnitude of potential cost savings on the table, this was a worthwhile endeavor, and turned out to be a rather successful undertaking. Fortunately, I work with a team of great individuals who adapt on the fly and work in an awesome fashion, so we've been able to spin up things like this with pretty much zero lag. 

When we order systems, we get them without an operating system, which saves us on the Windows licensing a bit. Sometimes doing this on a one-off system is difficult, but when you're ordering in bulk you have more wiggle room. Between Google Docs and Libre Office, we've saved even more. I won't even get into the cost savings vs having a fleet of Apple systems, as that's an obviously huge factor as well that I'm sure everybody can understand.

Currently we have in the neighborhood of 1,800ish (I believe) systems running Ubuntu 12.04 + our XFCE desktop. In about two weeks, we will be receiving 1,700 more systems as part of a high school 1 to 1 initiative, which will supplement each student with a dual core Acer laptop in the area of 11-12" screens. Acer is a company that I used to have a low opinion of, but lately I feel like Acer has been coming out on top with some of the systems they've been putting out there. Their support is really good as well, which is an area of frustration with some other big name companies (then again, which company out there doesn't have SOME level of support issues at times). All in all, while we considered many brands, Acer just had more to offer at a better price with better support. On top of that, they understood our Linux goals, unlike a certain Chinese manufacturer that starts with L (ahem) that was (surprisingly) a rather big let-down in some ways. These systems will be in replacement to the otherwise inevitable need to upgrade our laptop carts in the high school, which are older white Macbooks that have just left sight of support from Apple in regards to updates, etc.

For now, our Linux based systems are relegated to student usage only. Our staff are still on a mixture of newer Macbook Pros and Windows 8 powered systems. Each operating system has pros and cons, but being able to transition the vast majority of our systems (aka student systems) has offered tremendous long term flexibility and savings. We have issues with our Linux systems at times, but we have issues with our Mac and Windows systems too. It wouldn't surprise me if, in time, we entertain the idea of moving staff to Linux based systems on a future system refresh. For now, there are certain things in the educational realm that restrict us to Win/Mac systems. These things admittedly anger me as I believe in using more open standards and web oriented solutions, but upper education which the state level government has a hold of can, well, drag their feet at times. Things have gotten far better in recent times though. As an example, an Ubuntu/Deb based client was recently released for some of our state-mandated testing, which is pretty much the definition of awesome and a sign that good (and compatible) things are only going to keep coming.

Here are some links for those interested.

[http://opensource.com/education/13/8/open-source-penn-school-district](http://opensource.com/education/13/8/open-source-penn-school-district)

[http://lancasteronline.com/article/local/827998_Penn-Manor-outlines-laptop-plans.html](http://lancasteronline.com/article/local/827998_Penn-Manor-outlines-laptop-plans.html)

[http://lancasteronline.com/article/local/719017_Penn-Manor-schools-boost-technology--toss-paper.html](http://lancasteronline.com/article/local/719017_Penn-Manor-schools-boost-technology--toss-paper.html)

[http://lancasteronline.com/article/local/909164_Penn-Manor-laptop-pilot-program-going-smoothly--board-learns.html](http://lancasteronline.com/article/local/909164_Penn-Manor-laptop-pilot-program-going-smoothly--board-learns.html)

After typing this out and researching these links I had one of those philosophical epiphanies of realizing just how much I love my job. :)

---

