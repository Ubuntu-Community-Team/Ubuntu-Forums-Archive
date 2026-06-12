---
title: "Thunderbird 3.0 e-mail from Thyunderbird 2.0x"
date: 2010-02-15
forum: Ubuntuzilla
---

### Post by tractor on 2010-02-15
Hi,

I was trying to upgade my brother's computer to Ubuntu 9.10 from Windows Vista. I had all of his e-mail from Thunderbird in Windows into Thunderbird 2.0.0.23 in Ubuntu. When Thunderbird 3.0 originally came out, I installed with the daily builds in Ubuntu 9.10 on my computers. The install automtically retrived my e-mail from 2.0.0.23 and indexed it into 3.0. I had assumed the same would happen with installing the Thunderbird build from Ubuntuzilla, but it did not. I didn't want to put the daily builds on his computer. I tried copying his entire profile to the new Thunderbird folder, ./thunderbird. I tried replacing the mail folders in the default 3.0 profile with the folders in his profile. I got a few things to show up, but not most. After several hours, I gave up. His total profile folder size is 5.2 gigs due to his work. I think the issue is that just copying the profile to Thunderbird 3 is a problem since the e-mail isn't indexed for the new search in Thunderbird 3. Any help you can give on getting his mail from 2.0.0.23 to your build of 3.0.1 would be greatly apprecaited.

---

### Post by nanotube on 2010-02-15
Hi,

First, i must recommend you to make a backup of the current thunderbird profile, "just in case".

As far as getting the profile seen by the mozilla build, the easiest thing is to create a symlink from .thunderbird to .mozilla-thunderbird.

The ubuntu repositories version stores the profile in ~/.mozilla-thunderbird, while the mozilla build looks for it in ~/.thunderbird

So, the following code would place a link called .thunderbird, pointing at .mozilla-thunderbird, and when the mozilla build looks for the profile, it will get directed toward the .mozilla-thunderbird location.

so, assuming directory .thunderbird doesn't currently exist, and .mozilla-thunderbird does, and contains the profile data, issue the following command from the home directory:
```
ln -s .mozilla-thunderbird .thunderbird
```

then start tb3 and it should see and use the old profile.

---

### Post by tractor on 2010-02-15
Thank you so much. I will give it a try. I probably won't be back at his place until the end of the week to give it a try. Thank you again!

---

### Post by tractor on 2010-02-15
Just a brief note for nanotube. I see you are from PA. I'm from near Penn State in the central part of the state. I've been using Ubuntu for just under a year now. 90% + of my computer work now is done on it. I'm quite impressed with it, and have installed it on between 15 and 20 computers so far, all for free. I've come a long way, but have far, far to go also, like my initial post here shows. It would seem to me in this recession that a person would be able to make a side business of installing Ubuntu and open source software to help people save money and increase performance of older machines. It performs really well on 4 to 5 year old hardware, and is almost as fast as a new computer would be for most folks.

---

### Post by nanotube on 2010-02-16
> **tractor said:**
> Just a brief note for nanotube. I see you are from PA. I'm from near Penn State in the central part of the state. I've been using Ubuntu for just under a year now. 90% + of my computer work now is done on it. I'm quite impressed with it, and have installed it on between 15 and 20 computers so far, all for free. I've come a long way, but have far, far to go also, like my initial post here shows. It would seem to me in this recession that a person would be able to make a side business of installing Ubuntu and open source software to help people save money and increase performance of older machines. It performs really well on 4 to 5 year old hardware, and is almost as fast as a new computer would be for most folks.

keep up the good work! and good luck getting your business off the ground! :)

---

### Post by tractor on 2010-02-16
Hi Nanotube,


Thank you for your kind words!!!!!!! And your fix worked perfectly, instantly for the Thunderbird mail!!!!!!!! Now if I could just get his Brother printer to work. I've installed many HP's, some Samsung, a Canon, and a Kinoica-Minolta, and they all worked perfectly. Not this Brother though!!!!!!!!

Thanks again!!!!!!!

---

### Post by nanotube on 2010-02-17
> **tractor said:**
> Hi Nanotube,


Thank you for your kind words!!!!!!! And your fix worked perfectly, instantly for the Thunderbird mail!!!!!!!! 


excellent :)

> 
Now if I could just get his Brother printer to work. I've installed many HP's, some Samsung, a Canon, and a Kinoica-Minolta, and they all worked perfectly. Not this Brother though!!!!!!!!

Thanks again!!!!!!!

if you google around for "linux brother <modelnumber>", i bet you'll find something useful. if not, try posting in the general forums section, maybe someone will come up with something. :)

---

### Post by tractor on 2010-02-21
Hi nanotube (I'm sorry I don't know your name!),

I just wanted to give you an update on the Brother printer. I kept trying to find something on the net. I had done this before writing to you and afterwards also. I went through all of the things I could find on the Brother site. Still, I couldn't get it working. Yesterday morning I left a post in the Ubuntu forums. I've never had much success there. A post there disappears very quickly. Several hours later, I left basically the same post on the Ubuntu Launchpad forums under hardware. In all of my hunting around this past week, I did learn a lot, including about cups and learning about localhost:631. etc. I haven't had to use the forums too much since I started with Ubuntu. Normally in Google I find the answer to an issue in 5 or 10 minutes. Also, when I've used the forums, I've generally had much more luck in the launchpad forums. Last evening I had a response from the launchpad post suggesting going to the openprinting site with a specific link, and sort of suggesting I try the PPD file there. I downloaded that and installed it through localhost:631 and the printer is now working perfectly!!!!!!! I just thought you might like an update. Thanks again for everything!!!!!!!

---

### Post by nanotube on 2010-02-21
heh great news - glad you got everything sorted out! :)

---

### Post by tractor on 2010-02-25
Hi nanotube,

I do have a question about the Ubuntuzilla Firefox 3.6 build. The same holds true with the Namoroka daily build. If you go to [www.cbur-ruralproperty.com](www.cbur-ruralproperty.com) , you will see a java menu just under the logo, and also a marquee. These always worked fine in all Firefox versions through 3.5x in Ubuntu 8.10, 9.04, and 9.10. Last year I started getting the daily builds to get Thunderbird 3. You folks were still doing the script process. I have several folks I update for and didn't want to need to keep going back and updating the applications for them. I like your new repositories much, much better!!!!!!! Anyway, with the Thunderbird 3.0 I also started getting the daily builds of Firefox. That was ok. Everything was fine with the menu and marquee until the daily build (Firefox 3.5.8 pre) the day before Firefox 3.6 was released. Then I lost the Java, which your site shows me how to get it back. But once I had it back working, if you scroll down that page, big white blocks appear where the menu and marquee are. I've upgraded about 15 machines to Firefox 3.6 and in all cases I needed to apply your java fix, and in all cases when scrolling on the pages in that site the white blocks appear. As I said, this never happened in any of the Firefox 3.5x or earlier. It does not happen with Opera or the 4x and 5x linux versions of Google Chrome. If you have any problem reproducing it, I can send you some screenshots. Who should I report this too? It also happens with a totally different marquee used on [www.tripennucc.com](www.tripennucc.com) .

Thank you for your assistance.

---

### Post by tractor on 2010-02-25
Oops!!!! The marquees are not on the home page of [www.cbur-ruralproperty.com](www.cbur-ruralproperty.com) .

---

### Post by nanotube on 2010-02-25
hm, no idea... that site hung my browser completely. (when i enabled the java plugin and let it load, which i normally don't do because most java crapplets are completely useless)

---

### Post by tractor on 2010-05-03
I have now upgraded from Ubuntu 9.10 to 10.04. I'm using the Ubuntu Builds of Firefox 3.6 and Thunderbird 3.0 which were being used in 9.10. They transferred over fine. Do I need to uninstall those and install the ones in the software center in order to keep getting updates?

Thank you.

---

### Post by nanotube on 2010-05-03
Hi,
If you want to stay on the mozilla builds, you don't have to do anything. You'll keep getting updates through the ubuntuzilla repositories.

If you want to get back to the 'ubuntu repositories' versions, then you can uninstall the mozilla builds. (make sure to back up your thunderbird/firefox profiles, just in case something goes south when the ubuntu builds come in to look at them.)

---

