---
title: "Ubuntu sync with Android.  What's the status?"
date: 2010-01-17
forum: The Cafe
---

### Post by michaelcole on 2010-01-17
Hi, what's the status on Ubuntu syncing with Android?  I searched, but couldn't find anything definative.  

I want to get an Android phone (Droid, Nexus One, or next multi-carrier version), but don't want to sync using windows.

How is sync?
 - Music
 - Podcasts - audio and video  (this is biggest for me)
 - Contacts
 - Backups
 - Etc.

Thanks,

Mike

---

### Post by hanzomon4 on 2010-01-17
Music and videos are covered, for everything else just sync over the air via google(contacts, mail, calendar)

---

### Post by Kalibur on 2010-01-17
> **michaelcole said:**
> Hi, what's the status on Ubuntu syncing with Android?  I searched, but couldn't find anything definative.  

I want to get an Android phone (Droid, Nexus One, or next multi-carrier version), but don't want to sync using windows.

How is sync?
 - Music
 - Podcasts - audio and video  (this is biggest for me)
 - Contacts
 - Backups
 - Etc.

Thanks,

Mike

Hi Mike 

With applications like Evolution Mail or thunderbird you can sync your calender contacts and email using your googlemail detials very easily.  Rhythmbox can pick up your android phone and will allow your do drag and drop songs to and from you music collection and to the phone.  Podcasts I haven't played with yet.  You can browse the SD card in the phone like a memory stick so backing up on that level is easy.  As for backing up apps there are free apps that will allow you to backup to sd card then to your pc if you like.

Other more advanced things you maybe interesting in include
1 Remote controlling you mythtv box using the android phone
2 Streaming music and video from your network host to the phone
3 using ssh and telnet or even gui log onto you computer through you phone.
4 many other possibilities

Ps I have a G1 with android 1.6 but the nexus one is equally if not more capable.

---

### Post by swiftwood on 2010-03-13
can you sync them with an AOL account?

(yes, I have AOL, I've had it for years, so its staying.)

I know you can get AOL email on Evolution and AOL on an Android phone, but can you get them to sync?

---

### Post by Paqman on 2010-03-13
> **swiftwood said:**
> can you sync them with an AOL account?

(yes, I have AOL, I've had it for years, so its staying.)

I know you can get AOL email on Evolution and AOL on an Android phone, but can you get them to sync?

If you've got POP3 access to your AOL email, you're sorted. Just open a Gmail account and get it to retrieve all your mail from AOL and it'll show up on the phone.

---

### Post by Paqman on 2010-03-13
Oops, double post!

---

### Post by phen on 2010-09-27
Dear All,

I've read your answers with interest, but I am looking for a way to sync evolution with android WITHOUT any google tool. I dont use google to protect my personal data...

If there are possibilites to avoid google, i would love to buy an android phone..

---

### Post by Paqman on 2010-09-27
> **phen said:**
> I dont use google to protect my personal data...


Android is probably not the best phone OS for you then. You can use the apps on the phone itself without a Google account, but syncing to a PC will require you to use Google.

---

### Post by Johnsie on 2010-09-27
This is really something people in Linux development need to get a grip on. At the moment it's a bit of a mess. There is no consistency when it comes to syncing portable devices and they really should be these days.

Ubuntu needs to do this in a simple, sensible and direct way. It seems like we are playing catch up. Microsoft has had this capability in outlook for years with many different phones.

---

### Post by gdbutcher on 2010-09-27
I use Banshee to sync music and podcasts to my Nexus One. Its really easy to set up, and you can set it to sync automatically when you plug in your phone.

As for your contacts, calenders, emails etc I can't help you with that, I have a gmail account, so all my mail, contacts and calender sync automatically with the phone and Thunderbird using imap.

---

### Post by Paqman on 2010-09-27
> **Johnsie said:**
> Microsoft has had this capability in outlook for years with many different phones.

:confused:

Linux syncs to Android phones exactly the same way that Outlook does, through your Google account.

Ubuntu One is heading towards being able to sync to Android without Google. It only does contacts at the mo, but a full sync with Evolution would be a logical place to go down the road.

---

### Post by phen on 2010-09-27
thanks for all your answers.


> **Paqman said:**
> 
Ubuntu One is heading towards being able to sync to Android without Google. It only does contacts at the mo, but a full sync with Evolution would be a logical place to go down the road.

thats interesting. I think I would then use ubuntu one. Now I am wondering whether I should buy and hope for a solution or wait. I allways had bad luck with mobile phones. I've allways bought mobiles that were looking very good and had all the features, but with many hidden flaws.

this time I want to do good research beforehand. Since Android is allready Version 2 and hence mature, I thought it should be a good Os to go for.

bye

---

### Post by Paqman on 2010-09-27
> **phen said:**
> 
thats interesting. I think I would then use ubuntu one.

I'm just speculating though, i've got no special insight into what Canonical have actually got planned for Ubuntu One.

---

### Post by shiverfarms on 2010-09-28
I'm confused. When I plug in my brand new DroidX via USB cable, I get a Motorola folder in my Nautilus but when I open it up, I can't see any files, pictures, or music....is there something I need to install in 10.04 in order to be able to see those files or is there a "share" option somewhere in my Droid?  Thanks.

---

### Post by eb sol on 2010-10-04
when I plug my sony ericsson xperia x10 to my ubuntu 10.04 ..

Nautilus shows the phone memory ( read only ) which contains the windows application :(  and the external memory card ( read and write )...

But still I can't sync my contacts or calender .. :(

---

### Post by sideaway on 2010-10-05
I have a gmail account I don't really use for anything, just for SMS backup, calendar syncing, and Appmonster will backup apps and create apks you can keep on your desktop. Nandroid does ROM backing up without the use of external software.

Putting all that aside, if you care to root it, you can install Cyanogen Mod (if you buy a supported phone). It installs by default with OUT Google account sync. Think Android with absolutely no google or any third party dependence. It's truly a master ROM.
You can still retrieve AOL e-mails without a google account. I recieve POP3, IMAP and Exchange e-mails from three different addresses all without my google account ever being invlolved.

I love my HTC Desire :)

---

### Post by phen on 2010-10-05
> **sideaway said:**
> 
Putting all that aside, if you care to root it, you can install Cyanogen Mod (if you buy a supported phone). It installs by default with OUT Google account sync. Think Android with absolutely no google or any third party dependence. It's truly a master ROM.

Hi

Thanks for your answer. But now I'm wondering what "to root it" means? Is it necessary to jailbreak it like apple phones? 

if i do not root it, can i still leave the google apps untouched and install alternative software for email, navigation, calender etc?

Thanks,

bye

---

### Post by iceman30ad on 2010-10-05
yes you will have no problem with  installing anything on it.  you just cant un-install any default apps or choose your os/ with out going to root 
 wife got one and ive been playing with it. most will not need to root it to do what they want to do.  most of the time it will just be bragging rights

---

### Post by ColdFusionEESG on 2010-11-03
I think some folks are missing the boat here on syncing....

Issue 1: Google
--------------------------------------------------------------------------
Google is seen by many as evil and using their online suite of tools is totally unacceptable for privacy and data loss reasons.

So this method of syncing is not going to fly with this crowd (which I'm part of).
--------------------------------------------------------------------------

Issue 2: Any online data storage (the cloud)
--------------------------------------------------------------------------
See issue 1 above....this goes for syncing Evolution with UbuntuOne....it's still online and I am NOT placing my contacts online...period!
--------------------------------------------------------------------------

So we still need the good old method of direct syncing (like synCE but for Android) to allow people to keep their data private and still keep their phones in step with their PCs.

Yes the Google/UbuntuOne/Cloud route is excellent....unless you don't want your personal data online.  This is a perfectly acceptable stance to take and should be considered.

What I'm seeing currently is a big step backward....with Google owning people.

Thanks for reading

Cheers

---

### Post by aysiu on 2010-11-03
> **ColdFusionEESG said:**
> I think some folks are missing the boat here on syncing....

Issue 1: Google
--------------------------------------------------------------------------
Google is seen by many as evil and using their online suite of tools is totally unacceptable for privacy and data loss reasons.

So this method of syncing is not going to fly with this crowd (which I'm part of).
--------------------------------------------------------------------------

Issue 2: Any online data storage (the cloud)
--------------------------------------------------------------------------
See issue 1 above....this goes for syncing Evolution with UbuntuOne....it's still online and I am NOT placing my contacts online...period!
--------------------------------------------------------------------------

So we still need the good old method of direct syncing (like synCE but for Android) to allow people to keep their data private and still keep their phones in step with their PCs.

Yes the Google/UbuntuOne/Cloud route is excellent....unless you don't want your personal data online.  This is a perfectly acceptable stance to take and should be considered.

What I'm seeing currently is a big step backward....with Google owning people.

Thanks for reading

Cheers
It's perfectly acceptable to take that stance, but just don't expect Android (which is produced by Google) to make that stance easy to work with Android.

Android is designed to sync to the cloud.

What you want is the equivalent of making an electric car out of one designed to be powered by gasoline. If you want a local sync, buy a phone that uses an operating system *optimized* for a local sync.

If you truly believe Google to be evil, why would you want to use an operating system (Android) from Google?

---

### Post by ColdFusionEESG on 2010-11-03
> **aysiu said:**
> It's perfectly acceptable to take that stance, but just don't expect Android (which is produced by Google) to make that stance easy to work with Android.

Android is designed to sync to the cloud.

What you want is the equivalent of making an electric car out of one designed to be powered by gasoline. If you want a local sync, buy a phone that uses an operating system *optimized* for a local sync.

If you truly believe Google to be evil, why would you want to use an operating system (Android) from Google?

Oh I'm not naive....I know that Google wants to rule with an iron fist just like MS...doesn't mean I have to like it ;-)

Sorry, but your gas/electric analogy just doesn't do it for me.  BTW most hybrids currently have gas and electric...hehe

All I want to be able to do is use a device the way I WANT TO and not they way that allows a company to become a monopoly or to store MY DATA online.

There are things about Android that I do like (hell it is Linux after all), but just like with my current HTC Touch...I don't want the web on my phone (with the exception of getting apps of course...I don't browse/text/e-mail from my phone)....but I still like smart phones.  You can do more things with smart phones....and I also am looking at developing remote data collection apps for Android....so I need a test device.

Anyways...I'm done with explaining why.....it's what I (and my little searching has shown) many others want.

So if anyone has any ideas....please fire away...looking for solutions not debates ;-)

Cheers

---

### Post by aysiu on 2010-11-03
I don't want to debate either. I hope you do find a solution. I just think that if you don't there's a good reason why. The operating system is built to sync with the cloud.

---

### Post by phen on 2010-11-03
> **aysiu said:**
> 
What you want is the equivalent of making an electric car out of one designed to be powered by gasoline. If you want a local sync, buy a phone that uses an operating system *optimized* for a local sync.

If you truly believe Google to be evil, why would you want to use an operating system (Android) from Google?

your comparison is wrong. It is more like adding a power cord to an electric car which uses replaceable batteries out of the box.

providing means to sync directly to PC software is nothing more than providing a small app that takes contacts and other data and delivers them via implemented protocols to a private pc instead of a system somewhere on the net.

there already exist sync software for windows (from samsung and htc), the app for the mobile device side is there too. only the linux app is missing.

I would prefer using a truly open OS like meego, but its not ready yet. hence android is the most open system out there imho.

---

### Post by aysiu on 2010-11-03
> **phen said:**
> your comparison is wrong. It is more like adding a power cord to an electric car which uses replaceable batteries out of the box. Thanks. Much better analogy. Same point remains--people know going in that Google is involved and that Android syncs to the cloud. If you want to work some hack to sync locally instead, good luck. You just made extra work for yourself.

---

### Post by ColdFusionEESG on 2010-11-04
> **aysiu said:**
> ...If you want to work some hack to sync locally instead, good luck. You just made extra work for yourself.

Ya see...that's my point....I shouldn't have to "hack" as you say anything to do this....it is functionality that has always been there, but now with Android (the supposed open OS) you can't.

Cheers

---

### Post by ColdFusionEESG on 2010-11-04
> **phen said:**
> 
providing means to sync directly to PC software is nothing more than providing a small app that takes contacts and other data and delivers them via implemented protocols to a private pc instead of a system somewhere on the net.

there already exist sync software for windows (from samsung and htc), the app for the mobile device side is there too. only the linux app is missing.

Thank Phen....a much clearer explanation of the situation!

It really is too bad Linux continues to lag behind in the mobile arena.  SynCE is a reasonable solutions for Windows mobile phones, but even that is far less convenient than dare I say ActiveSync.

Oh well....I'll get it sorted one way or another

Cheers

---

### Post by aysiu on 2010-11-04
> **ColdFusionEESG said:**
> Ya see...that's my point....I shouldn't have to "hack" as you say anything to do this....it is functionality that has always been there, but now with Android (the supposed open OS) you can't.

Cheers
It has always been where? In Android? Are you saying Android used to have local sync and that Google intentionally removed it?

---

### Post by mcduck on 2010-11-04
> **ColdFusionEESG said:**
> Thank Phen....a much clearer explanation of the situation!

It really is too bad Linux continues to lag behind in the mobile arena.  SynCE is a reasonable solutions for Windows mobile phones, but even that is far less convenient than dare I say ActiveSync.

Oh well....I'll get it sorted one way or another

Cheers

I'd actually call any manual syncing with computers as "lagging in behind". Especially when the alternative is as good as it is, automatic syncing without any cables or any manual user interaction.

And no, not being able to do *whatever comes to your mind* is not a limitation of freedom, at least not in the sense the word "free" is used on free software (or any other use of "free" I can think of, really).

You are free to sync directly with your computer, nobody is stopping you from doing it. It's just that clearly nobody else is interested in doing so, you might have to make your own tools to do it. But you are free to do that.

If there was some built-in feature to explicitly prevent any syncing other than with Google's cloud, *that* would be a limitation on your freedom. But there isn't. :)

---

### Post by aysiu on 2010-11-04
My understanding is that Android (*sans* Google proprietary apps like Gmail, YouTube, and Maps) is open source, so I don't see how it could be limiting anyone's freedom.

If you are a programmer, take one of Cyanogen's rooted Android roms (the rom itself has no Google proprietary code--it's all open source) and tweak it to sync contacts locally.

If you're not a programmer, hire someone else to do it.

If you can't do it yourself or hire someone else to do it, then you have available to you only what's available to you. Sorry.

Here is how functionality comes about: [list][*]A volunteer out of the goodness of her heart decides it's useful and codes it in.[*] A corporation thinks the functionality is a good idea for business and codes it in.[*]A rich individual pays a programmer to code it in.[/list] There is no [list][*]Functionality magically drops from the sky because I think it's a good idea but don't want to do it myself or pay for it.[/list] option.

---

### Post by ColdFusionEESG on 2010-11-04
> **mcduck said:**
> I'd actually call any manual syncing with computers as "lagging in behind". Especially when the alternative is as good as it is, automatic syncing without any cables or any manual user interaction.

And no, not being able to do *whatever comes to your mind* is not a limitation of freedom, at least not in the sense the word "free" is used on free software (or any other use of "free" I can think of, really).

You are free to sync directly with your computer, nobody is stopping you from doing it. It's just that clearly nobody else is interested in doing so, you might have to make your own tools to do it. But you are free to do that.

If there was some built-in feature to explicitly prevent any syncing other than with Google's cloud, *that* would be a limitation on your freedom. But there isn't. :)

That's your opinion.  I think the cloud is a step in the wrong direction for privacy and data security.  I don't need my data online...I have portable devices...phone and laptop...why the heck would I need the cloud ;-)

As far as nobody being interested in doing it the way I want to....you should check some other boards....MANY cheesed off people just like me ;-)

---

### Post by ColdFusionEESG on 2010-11-04
> **aysiu said:**
> My understanding is that Android (*sans* Google proprietary apps like Gmail, YouTube, and Maps) is open source, so I don't see how it could be limiting anyone's freedom.

If you are a programmer, take one of Cyanogen's rooted Android roms (the rom itself has no Google proprietary code--it's all open source) and tweak it to sync contacts locally.

If you're not a programmer, hire someone else to do it.

If you can't do it yourself or hire someone else to do it, then you have available to you only what's available to you. Sorry.

Here is how functionality comes about: [list][*]A volunteer out of the goodness of her heart decides it's useful and codes it in.[*] A corporation thinks the functionality is a good idea for business and codes it in.[*]A rich individual pays a programmer to code it in.[/list] There is no [list][*]Functionality magically drops from the sky because I think it's a good idea but don't want to do it myself or pay for it.[/list] option.

Thanks for the lesson in software development....I am a programmer and I own a software development company ;-)

---

### Post by aysiu on 2010-11-04
> **ColdFusionEESG said:**
> Thanks for the lesson in software development....I am a programmer and I own a software development company ;-)
So go for it, then. Modify Android to locally sync. I'm sure a lot of participants in this thread would be appreciative of your efforts.

---

### Post by mcduck on 2010-11-04
> **ColdFusionEESG said:**
> That's your opinion.  I think the cloud is a step in the wrong direction for privacy and data security.  I don't need my data online...I have portable devices...phone and laptop...why the heck would I need the cloud ;-)

As far as nobody being interested in doing it the way I want to....you should check some other boards....MANY cheesed off people just like me ;-)

I don't need my data online either. I need up-to-date data on all my computers and devices, regardless of if they are in the same room and cable-legth apart from each other, and getting that without having to do any manual syncing is awesome.

If I was concerned about the security of Google's cloud, I sure wouldn't have bought an Android phone, knowing very well that greatest benefits of the platfrom come from the clod features.

What comes to people complaining about this on boards, in my experience most of them have been previous users of older smartphone platforms, so used to having to sync manually with some special program from the phone's manufacturer that they hadn't even realized they don't really need to do it in such a complicated way.

---

### Post by ColdFusionEESG on 2010-11-04
> **aysiu said:**
> So go for it, then. Modify Android to locally sync. I'm sure a lot of participants in this thread would be appreciative of your efforts.


It's a matter of time....not lack of desire ;-)

---

### Post by ColdFusionEESG on 2010-11-04
> **mcduck said:**
> I don't need my data online either. I need up-to-date data on all my computers and devices, regardless of if they are in the same room and cable-legth apart from each other, and getting that without having to do any manual syncing is awesome.

If I was concerned about the security of Google's cloud, I sure wouldn't have bought an Android phone, knowing very well that greatest benefits of the platfrom come from the clod features.

What comes to people complaining about this on boards, in my experience most of them have been previous users of older smartphone platforms, so used to having to sync manually with some special program from the phone's manufacturer that they hadn't even realized they don't really need to do it in such a complicated way.

Nothing that complicated about it....I sync a Windows mobile phone with Evolution now using SynCE....takes all of 1-2 minutes every so often....just no GUI for it which is my only real complaint.

Regardless....complexity is not my concern....privacy and controlling my own data is.

Cheers

---

### Post by arkroan on 2010-11-10
> **ColdFusionEESG said:**
> I think some folks are missing the boat here on syncing....

Issue 1: Google
--------------------------------------------------------------------------
Google is seen by many as evil and using their online suite of tools is totally unacceptable for privacy and data loss reasons.

So this method of syncing is not going to fly with this crowd (which I'm part of).
--------------------------------------------------------------------------

Issue 2: Any online data storage (the cloud)
--------------------------------------------------------------------------
See issue 1 above....this goes for syncing Evolution with UbuntuOne....it's still online and I am NOT placing my contacts online...period!
--------------------------------------------------------------------------

So we still need the good old method of direct syncing (like synCE but for Android) to allow people to keep their data private and still keep their phones in step with their PCs.

Yes the Google/UbuntuOne/Cloud route is excellent....unless you don't want your personal data online.  This is a perfectly acceptable stance to take and should be considered.

What I'm seeing currently is a big step backward....with Google owning people.

Thanks for reading

Cheers

+1 

And since this person has a Software Company, why not invest in an Android Sync application for Linux? 

I would love to help but my knowledge of Unix-Linux, Driver development, Kernel development is trivial.

With that said.. Is any Linux Guru and Android enthusiast planning to develop such a tool?? If there is anybody, I would love to help..

( My skills include C/C++ and just started learning to use GTK+ and Glade - no unix experience though )

---

### Post by ColdFusionEESG on 2010-11-10
> **arkroan said:**
> +1 

And since this person has a Software Company, why not invest in an Android Sync application for Linux? 

I would love to help but my knowledge of Unix-Linux, Driver development, Kernel development is trivial.

With that said.. Is any Linux Guru and Android enthusiast planning to develop such a tool?? If there is anybody, I would love to help..

( My skills include C/C++ and just started learning to use GTK+ and Glade - no unix experience though )

Glad to see someone else is picking up what I'm laying down!! ;-)

It's really amazing how many folks will freely give their data to a third party.

You know it hit me that if your government asked you to provide all the personal details that can be found in calendars and e-mail, the answer would be "not on your life big brother".  Now we have Google and because they make it "easy" people hand over the info freely....insanity (and don't get me started on Facebook....truly big brother....and yet....)

I'd love to make this syncing happen, but alas I'm a web guy....ColdFusion/JavaScript/jQuery/databases of all kinds/Adobe Flex/AIR.  So I don't know how much use I'd be.....but I'd still be interested it trying to make it happen.

Cheers

---

### Post by aysiu on 2010-11-10
> **ColdFusionEESG said:**
> 
You know it hit me that if your government asked you to provide all the personal details that can be found in calendars and e-mail, the answer would be "not on your life big brother".  Now we have Google and because they make it "easy" people hand over the info freely....insanity (and don't get me started on Facebook....truly big brother....and yet....) The government already has a ton of personal details about me. It knows where I live, where I vote, how much money I make, my marital status, birthday, what my bank is, etc.

The library knows what books I read and when I read them. My credit card company knows what I buy and how much I pay for it all. My email provider knows everything I email my friends about and who my friends are and how often I contact them. My ISP knows every single website I visit, how long I spend on each website, and how much I download from each website.

I don't see why Google gets singled out as being particularly evil. [Privacy on the Internet Still Doesn’t Exist](http://www.psychocats.net/ubuntucat/privacy-on-the-internet-still-doesnt-exist/)

---

### Post by ColdFusionEESG on 2010-11-10
> **aysiu said:**
> The government already has a ton of personal details about me. It knows where I live, where I vote, how much money I make, my marital status, birthday, what my bank is, etc.

The library knows what books I read and when I read them. My credit card company knows what I buy and how much I pay for it all. My email provider knows everything I email my friends about and who my friends are and how often I contact them. My ISP knows every single website I visit, how long I spend on each website, and how much I download from each website.

I don't see why Google gets singled out as being particularly evil. [Privacy on the Internet Still Doesn’t Exist](http://www.psychocats.net/ubuntucat/privacy-on-the-internet-still-doesnt-exist/)

First off....the big companies get singled out because they are the BIG companies...pretty simple really...they have the most impact.  Hey...I know privacy to a certain degree is long since dead...I'm NOT that naive....but I sure as hell will protect myself to the best of my ability....I don't roll over like many sheeple out there.

Those are disparate organizations and are basic details that have been out there for a very long time.  Think about one organization knowing ALL those details.

I'm talking about profiling....

Listen...Google can aggregate info about you from many activities you perform in the cloud....read your e-mail...associate you with others....and that's when it gets scary.  Facebook is even worse for this....you are linked to all the people you associate with...paints a lovely picture for those wanting to use this data.

OK...let's look at Google Calendar and the safety of its users.  If you publish your calendar so others can see it and book an appointment to meet someone at a certain address at a certain time.  You have now told the world where that other person will be and when (and there is nothing they can do about it).  Now what could you do with that info?  Well...rob their house while they aren't home....meet them where they will be to do something nasty.  This sort of thing has already started occurring with people saying they will be on vacation on Facebook and having their homes robbed.

These are valid concerns to those that are paying attention.  Just because maintaining your privacy is hard doesn't mean it's a bad move.

Cheers

---

### Post by aysiu on 2010-11-10
> **ColdFusionEESG said:**
> First off....the big companies get singled out because they are the BIG companies...pretty simple really...they have the most impact.  Hey...I know privacy to a certain degree is long since dead...I'm NOT that naive....but I sure as hell will protect myself to the best of my ability.... My ISP is also a big company, and yet Google gets a lot more attention than my ISP does. My ISP also knows every single website I visit or download from. Google does not.

> I don't roll over like many sheeple out there. Please stop calling people "sheeple" who disagree with you and decide to use Google services. If you continue to keeping calling me and other Google users "sheeple," I will just give you an infraction for personal insults.

> 
Listen...Google can aggregate info about you from many activities you perform in the cloud....read your e-mail...associate you with others....and that's when it gets scary.  Facebook is even worse for this....you are linked to all the people you associate with...paints a lovely picture for those wanting to use this data. I'm aware of all this, and I still use Google and Facebook. My world will not end tomorrow. No need for the alarmism.

> OK...let's look at Google Calendar and the safety of its users.  If you publish your calendar so others can see it and book an appointment to meet someone at a certain address at a certain time. If you publish your calendar so others can see it, then that's your decision to broadcast it to the world. The only people who can see my Google Calendar are Google, me, and my wife.

> This sort of thing has already started occurring with people saying they will be on vacation on Facebook and having their homes robbed. But that's not a problem inherent in Facebook. That's a problem with how people are using Facebook.

> These are valid concerns to those that are paying attention.  Just because maintaining your privacy is hard doesn't mean it's a bad move. Maintaining your privacy isn't hard, actually. Having total privacy is almost impossible, though, and the illusion that simply avoiding Google means you're free from corporations and governments knowing what you do is not going to make your life any better.

---

### Post by Paqman on 2010-11-10
> **ColdFusionEESG said:**
> 
It's really amazing how many folks will freely give their data to a third party.


Not freely at all. It's a fair exchange. We agree to provide a peek into our lives and in return we get excellent services for free.

There's nothing underhand going on, it's always been quite clear that's what the deal was. If you don't agree, then you don't use Google services (such as Android phones). Simple.

Just about everybody you deal with online will be profiling you anyway. If you don't like it, you're going to find it increasingly difficult to use online services. Personally I don't care that Google, Amazon, Tescos and Visa are profiling me, as long as they continue to prove their security is up to snuff.

---

### Post by aysiu on 2010-11-10
I'd really like to separate out general discussion about Google and Android from *productive discussion about actually setting up offline syncing*, so I'm splintering off a new thread for the latter endeavor:
[Project: Off-link sync for Android](http://ubuntuforums.org/showthread.php?t=1618443)

---

### Post by ColdFusionEESG on 2010-11-10
> **aysiu said:**
> My ISP is also a big company, and yet Google gets a lot more attention than my ISP does. My ISP also knows every single website I visit or download from. Google does not.

Your ISP is not actively mining this data and aggregating and cross-referencing it with other data.  Your ISP can tell that someone at your IP went to whatever sites they went to.  They have no idea if it was you, your wife/kids/neighbour stealing your signal (just a log).  So the usefulness of that data is in question.

BTW you made the assumption that all I mean is Google.  I mean ALL social media and cloud computing.

 > **aysiu said:**
> Please stop calling people "sheeple" who disagree with you and decide to use Google services. If you continue to keeping calling me and other Google users "sheeple," I will just give you an infraction for personal insults.[\QUOTE]

Fair enough...apologies....to be clear it was never directed at you or anyone in particular.  There is a non-technical segment of the population (quite a large segment) that simply does not understand what they are really doing when they use these types of services.  Do you think they are REALLY deciding it's OK to give up their privacy and data? or do they just see the service as handy and sign up?  Feel free to hand out infractions if you so desire.

[QUOTE=aysiu;10099010] I'm aware of all this, and I still use Google and Facebook. My world will not end tomorrow. No need for the alarmism.

It's a free planet and I can say what I want.  My opinion is that this is not alarmism....it's fact.  What I am talking about has happened already.

I'm glad you are happy with giving it up to big brother...that is 100% your right.

> **aysiu said:**
> 
 If you publish your calendar so others can see it, then that's your decision to broadcast it to the world. The only people who can see my Google Calendar are Google, me, and my wife.

 But that's not a problem inherent in Facebook. That's a problem with how people are using Facebook.


You missed my point.  You can expose SOMEONE ELSE without their consent.  It's like Facebook location stuff and FourSquare.  Other people can tag your location without your consent....very dangerous stuff.  On the surface it's all fun and games....but just think of the nastiness this kind of functionality can be used for.  You may want to re-read my scenario.


> **aysiu said:**
> 
 Maintaining your privacy isn't hard, actually. Having total privacy is almost impossible,


Well it sure is getting harder now isn't it... ;-)

> **aysiu said:**
> 
 though, and the illusion that simply avoiding Google means you're free from corporations and governments knowing what you do is not going to make your life any better.

I humbly disagree and clearly anything I say is not going to matter to you.  I never said it was only Google...I said the cloud....and I will continue to avoid it like the plague.

Cheers

---

### Post by ColdFusionEESG on 2010-11-10
> **Paqman said:**
> Not freely at all. It's a fair exchange. We agree to provide a peek into our lives and in return we get excellent services for free.

There's nothing underhand going on, it's always been quite clear that's what the deal was. If you don't agree, then you don't use Google services (such as Android phones). Simple.

Just about everybody you deal with online will be profiling you anyway. If you don't like it, you're going to find it increasingly difficult to use online services. Personally I don't care that Google, Amazon, Tescos and Visa are profiling me, as long as they continue to prove their security is up to snuff.

You assume most people even understand the nuances of the deal.  I put forward that a large portion of the population does not.

....and since when have the proved their security is up to snuff??

Facebook privacy concerns....have a look online and read all the issues of data leakage and third-party abuse.  Google...hmmm...street cars collecting wireless network data they should not.  Microsoft....lost all the contact data for thousands of smartphone users that was backed up in the cloud.

...and so on..please man...check your facts

....but hey...glad you are happy with it...all the power to you!

Cheers

---

### Post by ColdFusionEESG on 2010-11-10
> **aysiu said:**
> I'd really like to separate out general discussion about Google and Android from *productive discussion about actually setting up offline syncing*, so I'm splintering off a new thread for the latter endeavor:
[Project: Off-link sync for Android](http://ubuntuforums.org/showthread.php?t=1618443)

LOL...I said I didn't want to debate it and yet you kept coming at me....

nuff said

Cheers

---

### Post by lotech on 2011-06-20
Ok, I am just another one out of the few that own an Android phone, but don't really enjoy it synchronizing my personal data online. I do have a Gmail a/c but mainly for downloading apps and update phone s/w use, it seems the OS by default synchronize the contact to Google, I have about 100 contacts, for unknown reason after some use I got over 300 contacts, there are duplicates I need to manually delete this is really annoying, not to mention there is no way(?) to backup the calender without using Google.

I just wondering if it is possible to synchronize my contact and calender to my web host, via FTP or some kind of remote drive, any idea ?

---

### Post by joshp1 on 2011-06-22
I know this is a old post, android syncs automaticly with Google cause Google owns and made Android. If you don't like it by a blackberry,Iphone, or palm. Also you can use yahoo and AOL,to sync your Calendar, and email.  You will need a Google account for Google android market place. I tried installing htc sync with wine but it wont open out of the wine system tray.

---

### Post by mschering on 2011-08-23
You can also use Group-Office to synchronize your android phone. You can install it on your own ubuntu server or any other linux distro. Check it out at [http://www.group-office.com](http://www.group-office.com)

---

### Post by forrestcupp on 2011-08-23
> **mschering said:**
> You can also use Group-Office to synchronize your android phone. You can install it on your own ubuntu server or any other linux distro. Check it out at [http://www.group-office.com](http://www.group-office.com)

Yeah, but who wants to pay 10 Euros per month for 512MB of data syncing?

---

### Post by ColdFusionEESG on 2011-08-23
.....and it's still a cloud/online solution isn't it.....just want simple local non-online syncing

Thanks for the idea....even if a tad spammy ;-)

Cheers

---

### Post by mschering on 2011-08-24
Sorry, I did not want to spam. I just thought it would be a good alternative for Google if you are concerned about your privacy. You can put the data on your own server.

---

