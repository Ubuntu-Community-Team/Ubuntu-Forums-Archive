---
title: "Ubuntu wins me over again"
date: 2008-08-04
forum: Testimonials &amp; Experiences
---

### Post by blueturtl on 2008-08-04
I am posting this to let everyone know that even after years of dedicated use Ubuntu still manages to surprise. I've been a member of these forums and a dedicated user for a few years now already. My household knows Windows only through a virtual machine. My friends and family have been targets of passive Ubuntu marketing for a while already. Passive, because I believe in choice and also because I know Ubuntu is not perfect.

That said I am also the family administrator and when people call me for support I always wish they were running Ubuntu instead of Windows. My siblings in particular really only use their machines for regular tasks which Ubuntu is more than well suited for. My little sister had received a fairly old system about six months ago (we're talking PentiumIII 1 GHz, GeForce3 etc). Of course the family wanted it set up with Windows XP "because everyone else has it, and because she needs MS Office for her school work". I didn't argue and set it up for them. I took extra care to make sure they wouldn't run into the usual problems with malware and other things.

Almost six months pass and I get a call telling me "the system has collapsed". Something really quirky was going on; my sister could log in, but the Start menu wouldn't show up, many programs were failing and sound was gone. My mother who also had an account on that system could no longer log in at all. To me the signs were clear, this had to be a dying hard-disk problem. So during our weekend visit I run the Ubuntu Live-CD which works just fine and backup all their data to the family server (already running Ubuntu). I know a Windows reinstallation awaits, but I also know it takes two days to restore the system to a fully functional status. Since the Ubuntu Live-CD was working so nicely I then suggested we install the system for a week to make sure the hard-disk was to blame. The system would probably have reduced functionality but at least my sister could browse the web and chat with her friends.

It only takes two hours and the system is set up. Expecting trouble I tell her that the system might stop working during the week since the hard-disk may be broken and also that certain things like her web cam and iPod probably won't work with Ubuntu without additional set up. I also tell her I'd look into salvaging her Thunderbird email from the backup server a little later (not knowing how to do that of course).

The week passes and the system works just fine. Nothing wrong with the hard-disk, apparently Windows had developed an internal issue and commited suicide. Hoping that maybe I wouldn't have to set up Windows again I start looking if I could overcome the barriers for using Ubuntu on this particular machine. Over our next visit I start looking into the iPod thing and turns out all that had to be done was re-initialize it on another system running iTunes. After that Ubuntu recognized it without a hitch, it mounted and she was able to use Rhythmbox to play and manage her music. Knowing the nightmare that webcams are I was already looking for ways to compile and install webcam drivers before the visit. Once there I tried cheese first and it turns out her webcam (Creative Vista Plus) was fully functional all along! I configured aMSN for her so she could make use of it. I then look at her salvaged Thunderbird account. I had a good feeling about it, so I simply pointed her Thunderbird profile folder towards the old one and it worked flawlessly. I managed to transfer all her email, account settings and address book by pointing .mozilla-thunderbird folder to her old folder profile folder from the Windows system! Now this is interoperability! With a closed source application transferring her mail and settings over would have been hell.

I then point her to OpenOffice for her school work, enable Compiz which runs surprisingly fluently on her ancient GeForce3 Ti200. I ask my sister if she'd want to keep using Ubuntu seeing as it was already set up and installing Windows would mean having to wait a few more days again and she says yes.

What happened to the original Windows install is a complete mystery, but it opened my eyes again to how much Ubuntu and Linux has accomplished on the desktop. Setting up Ubuntu was a lot easier than I expected even with all my experience, and now I have yet one less machine for which I will be receiving these support phone calls. Thanks Bill, this convert is on you!

---

### Post by stinger30au on 2008-08-04
converting email from outlook express to thunderbird is no big deal ,there is a converter in thunderbird to do this.

the main thing is so long as you can get xp to run then oyu can install thunderbird and get it to salvalge the data from outlook and merger it to thunderbird. the save this data to cd/dvd/thumb drive /server/ whatever and install ubuntu and restore from there.

glad it all worked out

---

### Post by armandh on 2008-08-04
sure 2 gig is better than 1 but those P-IIIs are a rock solid end of the line of rock solid processors. I have a 933 with Ubuntu feeding media to the family room tv [ntsc]. 

Ubuntu keeps that old hardware feeling like new.

I was thinking of all the hilarious ads I could write along the lines of ED meds.

---

### Post by blueturtl on 2008-11-14
This is a follow-up to the original story.

We stumbled on a really good offer for a Toshiba brand laptop at a local super market. I'm really not the type who's in to buying computer hardware from these places but the price was right and my sister has been dying for a portable for a long time. We decided to take the risk and (collectively) get it for her as a Christmas present. With limited details on the hardware it was impossible to do research on it beforehand, plus the notebook was a limited-time-offer so we had to act fast.

Since the hardware information at big stores is often quite limited, all I knew about the laptop was that it came with an AMD Sempron processor and 2 gigs of RAM. Plenty of power to replace her old Pentium3 I thought. The only question in my mind was -- since this thing came with Vista -- would it run Ubuntu? The reason I wanted that backdoor was because of the bad rep Vista has, I haven't really used it myself too much. Also by now my sister is used to Ubuntu and might want to keep it.

So I give the notebook a whirl. I want to set it up so to work properly before my sister unwraps it. Who'd want to spend Christmas downloading upgrades and patching, right? Vista fires up from a recovery partition and asks which language I want. I select Finnish. An hour or so later Vista has finished (pre)configuring. It's really really slow. I know this is a budjet computer but I can't help feeling Toshiba didn't really think about the end-user experience with this one. The hard-disk led refuses to go off and the system is running with 2 gigs or RAM! Also the desktop is cluttered with advertising for all sorts of things, including a free McAfree AV trial. I clear the desktop and try to join our wireless network to patch up Vista for the first running. Every time I try to join the wireless network the connection wizard bombs me with 'network was out of reach' or something similar. I wonder if that's really the case as I'm sitting on the floor right next to the router.

That gut feeling is creeping up so I dig up my Intrepid Ibex CD and fire it up. Shortly after Ubuntu comes up in all it's glory. The screen resolution is spot-on, I hear sound, even Compiz is working right out-of-box! Turns out the new open-source ATI drivers are already here and this laptop happens to have an ATI video card. I'm feeling lucky so I check network manager for wireless networks. None are detected. I expected as much. I plug the lappy in with a cord and start browsing for solutions. I quickly stumble on the compat-driver pack which updates Ubuntu with more resent wireless modules. A reboot later I have working wireless! I decide to go on with the installation. I'd leave my sis with a dual-boot option. If she ever wanted she could run Vista, or if she preferred Vista, she'd have Ubuntu as a backup system.

I resize the partitions with Ubuntu's Partition editor. This thing has a separate NTFS partition for user data. She can access her files from both Windows and Ubuntu, great! All I needed to do was nibble on Vista's partition a bit to make room for Ubuntu.

The notebook really only has two components that traditionally give Linux users hell; one is the built-in wireless, the other is the built-in web cam. Surprisingly what initially gave me trouble was DVD playback. Even with libdvdcss installed I was getting messages about not being able to read the DVDs I was throwing at the computer. After another quick Google revealed that the new ATI open source driver needed to have a newer 'EXA acceleration method' manually enabled in xorg.conf. Once the new AccelMethod enabled I was able to play DVDs and run 'cheese' to find out that the web cam was also fully working. No configuration necessary.

Did we get lucky, or is Ubuntu's hardware support better than ever? What ever the case, a very merry Christmas awaits my little sister. :)

p.s. The notebook is a Toshiba Satellite L300 series with
AMD Sempron 2 GHz CPU
2 GB DDR2 memory
160 GB HDD
Dual-Layer DVD burner
ATI Radeon X1250 graphics, 15" screen
Realtek Wired/Wireless networking
Chicony built-in web camera

The only untested features are suspend/hibernate.
The cost was little more than what the so called "mini laptops" here are, at 445 euros.

---

### Post by stalkingwolf on 2008-11-16
Thats great .  I have an old tecra 8200 that is running 8.04.  I also have
an Everex stepnote that wont install anything but XP home, so far.  I am going to give one of them to an old friend of mine.  He wants the everex
but may get the Toshiba.  If I cant get Ubuntu to work.  His last "computer
training" was 35+ years ago.  It took 2 days for him to learn how to find and play Majoong.  So as he lives in Bakersfield CA and I am in AZ It has to be right before He leaves here.

Well see I am rather stuborn.  A case in example is we Just returned from
a 2 day trip to Tucson and Tombstone.  While there we visited My Aunt who is
as I recall 84 years old.  She needed a power wheel chair. She is covered by
insurance and medicare and has a letter from her DR. stating that a power chair is Required.  She has been housebound for at least 7 months while fighting with hoverround and others to get a chair, and being told ,"you have the wrong policy and by Hoverround You need to pay a 1300.00 copay. And so fourth.

It is a tradition in my family when ever someone goes to Tucson we all go out to a certain Mexican Restruant for dinner.  We Have been doing this 
as far back as I can recall, Im 53.
We get in late the first night an go for a visit.  We tell her we'll go to 
molina's tomorrow for dinner.   My Auny gets this strange sad look and says well I dont know .... . I tell her dont worry we'll figure something out.

Next morning we are planning to go to Mission San Xavier , My Wife has only seen pictures of it. And to Old Tucson.  While we are having our coffee
and breakfast I setup my laptop and connect to the wifi next door at the Chineese place ( the have a better connection than the hotel) and start looking for someplace  to rent a chair. I decide what the hell, and pull up craigslist.  Wonder of wonders there is a guy on the other side of town that has 3 for sale, power chairs. HMMM!  We call,  in a few minits he calls back, " Who are you and where are you? I tell him who I am and that I saw his listing on Craigs list.  

Turns out he is a repair business that works on medical equipment.  He gives me directions, cool he on the way to the Mission.

We get there , He has 2, one works, one he thinks needs a battery.  Shows us that the one works.  Wants 350.00 for both.  WOW. OK can you deliver? 
TODAY?   HMM Maybe there are only 2 of us and it is Friday our busiest day.

Damn gotta have the good one today.  Scratch head , wonder will it go in the Jeep?  Lets go look.  Take out my Visa and we go look.  Yep it will go.

OH by the way we don't take credit or debit cards can you write me a check?
( He already knows we live by Sedona)  Well Duh sure.  Ok we will put the good one in the Jeep and the will deliver the other Monday.

Bobs your uncle and off we go.  I tell my Wife we may not make the misson this time, She looks at me and tells me , "Thats OK were on another Mission." God , I Love my Wife.  My friend says Old Tucson will be there next time.

Short end to the story We didnt make the mission, We didnt make old Tucson,
We did make one elderly Lady very happy.  The last thing she said to Us
before we left to come home was " you gave me my Life back."  What more could you ask from a vacation?

So as you see I am stubborn that way.  The last thing I said was, " When all those sales people call back tell them to P*** off.  My Nephew did in
8 hrs what you couldnt do in 7 mos.

And knowing my Aunt she will.

Never give up.

---

### Post by 73ckn797 on 2008-11-16
WOW!

That ought to be an infomercial for Ubuntu.

---

