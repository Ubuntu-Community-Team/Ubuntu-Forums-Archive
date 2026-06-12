---
title: "Ubuntu CE v2.1 (Edgy) Preview"
date: 2006-12-12
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-12-12
*Just when I think I am going to take a break...* :D

I am working on the next release of Ubuntu CE. I am making some nice changes and additions.

First both the Dapper and Edgy version will include the updated Dansguardian GUI that includes the ability to disable Dansguardian. This does not completely disable it. It simply allows Firefox to surf without the filter.

I am also going to update the convert_me and upgrade_me scripts for both the Dapper and Edgy version to better integrate the Ubuntu CE themes into the users default installation.

Now for the bigger changes to the Edgy version!

The Edgy version will include an updated Daily Bible Verse (gVerse) program. There have been some bug fixes (thanks xfceslacker) and some clean up to the verse formatting. 

The [Virtual Rosary]("http://www.virtualrosary.org/") program will also be included in the Edgy version. Wait, you say. That is a Windows program. Yes, it is a Windows program, that is being integrated into Ubuntu CE (Edgy) using [Wine]("http://www.winehq.org/"). I had thought about building a Linux version of the program, but the Windows one runs so well under [Wine]("http://www.winehq.org/") that I would use it. I know that some will probably have a big issue with this, but I believe that it only shows more of the power of Linux. 

A new desktop configuration will also be implemented in the next release of the Edgy version. It will take on a more familiar look and feel for those that are used to Windows. Again, I know that many will balk at this idea, but one of the main goals of the Ubuntu CE project is to bring Linux to Christians who have never used Linux. There are many that will see the differences in the basic layout and run for the hills. I just want to make the transition more comfortable. For those that are already using Linux and do not like the idea of their desktop looking more "XP-ish" then I figure they probably already know just how easy it is to customize it.

I have attached screenshots of the [Virtual Rosary]("http://www.virtualrosary.org/") program running on the proposed Ubuntu CE v2.1 (Edgy) as well as one of the new desktop configuration.

I would love to hear from you all on the new changes.

God Bless, Jereme

---

### Post by daniminas on 2006-12-12
It looks nice.. ;) .. what about The Virtual Rosary program translations?

I'm spanish speaker and may be can help... :rolleyes: 

Good luke!

---

### Post by finferflu on 2006-12-12
I think protestants will not be happy with that, maybe there should be a prompt asking for the orientation of one's Christianity.

It's not a flame, it's just that I come from a protestant background, and I know how they react. I'm actually proposing your project to conference leaders. So I don't want them to be discouraged installing Ubuntu because of a Rosary.

Thank you!

And very nice wallpaper, by the way ;)

---

### Post by mhancoc7 on 2006-12-12
> **daniminas said:**
> It looks nice.. ;) .. what about The Virtual Rosary program translations?

I'm spanish speaker and may be can help... :rolleyes: 

Good luke!

Thanks for your kind words. I am not sure about translations for the Virtual Rosary program. I have attempted to contact the developer but I have not heard back. I believe the development may have stopped. :(

> **finferflu said:**
> I think protestants will not be happy with that, maybe there should be a prompt asking for the orientation of one's Christianity.

It's not a flame, it's just that I come from a protestant background, and I know how they react. I'm actually proposing your project to conference leaders. So I don't want them to be discouraged installing Ubuntu because of a Rosary.

Thank you!

And very nice wallpaper, by the way ;)

I appreciate your concerns. I do anticipate a possible backlash. However, one of the goals of Ubuntu CE is to be a resource for both Protestants and Catholics. Some Catholics might be offended that the KJV is installed by default as well. I think that it would be wrong to make it seem as if the "Catholic programs" are not ok to include by default. I think the same about the "Protestant programs" as well.

I hope that makes since.

God Bless, Jereme

---

### Post by daniminas on 2006-12-12
> **mhancoc7 said:**
> Thanks for your kind words. I am not sure about translations for the Virtual Rosary program. I have attempted to contact the developer but I have not heard back. I believe the development may have stopped. :(


Ok, in this [link ]("http://www.virtualrosary.org/modules.php") are some translatios... ;)

---

### Post by mhancoc7 on 2006-12-12
> **daniminas said:**
> Ok, in this [link ]("http://www.virtualrosary.org/modules.php") are some translatios... ;)

Thanks so much for finding the link. I was pretty sure that I remembered seeing that but I just wasn't sure. :)
God Bless, Jereme

---

### Post by doobit on 2006-12-12
> **mhancoc7 said:**
> Thanks for your kind words. I am not sure about translations for the Virtual Rosary program. I have attempted to contact the developer but I have not heard back. I believe the development may have stopped. :(



I appreciate your concerns. I do anticipate a possible backlash. However, one of the goals of Ubuntu CE is to be a resource for both Protestants and Catholics. Some Catholics might be offended that the KJV is installed by default as well. I think that it would be wrong to make it seem as if the "Catholic programs" are not ok to include by default. I think the same about the "Protestant programs" as well.

I hope that makes since.

God Bless, Jereme


Jereme,

Thanks for your continued work on this. Could you possibly test the Dansguardian scripts with Xubuntu to see if you can resolve some of the issues with that? I am also installing both Gnome and XFCE on one machine to see if all of the necessary dependancies are in place for it to work that way. 
I would like to be able to use the script on an Xubuntu base install, however, since most of my computers are low-power, slower speed machines. Currently, the disable and enable buttons work, but the blacklist/whitelist buttons don't work.

I will also test in Portuguese since that is my second language.

Is there a way we could have a choice when we install as to what Bible versions we could include in GnomeSword and whether or not to include the Rosary?

If that is too much trouble, then maybe the first page that opens after an install should quote John 17:20-21, and inform people that they can uninstall what they don't want. :)

---

### Post by potrick on 2006-12-12
Looking good, man. Not really sure if you can copy the "start" menu look from a copyright standpoint, you might want to think about that one. I'm sure there was a lot of discussion involved before you switched to a more windows-esq look, so I'm not going to get into it.

I do believe, however, that if you're going to be running wine programs inside ubuntu by default you should consider skinning the program by default. There are a couple methods to doing this on the forums and it would make the Windows app seem less alien to the environment. I think the two methods are using winecnf to set up a .msstyle file as the look for Windows program and another thread makes it possible to simply pick a colour skin for wine. I'd look them up for you, but I need to get back to my studies and really shouldn't have logged into the forums in the first place. 

Anyway, blessings on your work.

---

### Post by mhancoc7 on 2006-12-12
> **doobit said:**
> Jereme,

Thanks for your continued work on this. Could you possibly test the Dansguardian scripts with Xubuntu to see if you can resolve some of the issues with that? I am also installing both Gnome and XFCE on one machine to see if all of the necessary dependancies are in place for it to work that way. 
I would like to be able to use the script on an Xubuntu base install, however, since most of my computers are low-power, slower speed machines. Currently, the disable and enable buttons work, but the blacklist/whitelist buttons don't work.

I will also test in Portuguese since that is my second language.

Is there a way we could have a choice when we install as to what Bible versions we could include in GnomeSword and whether or not to include the Rosary?

If that is too much trouble, then maybe the first page that opens after an install should quote John 17:20-21, and inform people that they can uninstall what they don't want. :)

Thanks for your kind words and for your feedback.

I believe the problem that you are having with the Dansguardian script on Xubuntu may just be that you need gedit installed.

Let me know if that fixes it.

Well, I think I will consider your second suggestion regarding the software install. I might be able to easily add the prompt to let users know more about what is installed and that they can easily remove the unwanted packages.

> **potrick said:**
> Looking good, man. Not really sure if you can copy the "start" menu look from a copyright standpoint, you might want to think about that one. I'm sure there was a lot of discussion involved before you switched to a more windows-esq look, so I'm not going to get into it.

I do believe, however, that if you're going to be running wine programs inside ubuntu by default you should consider skinning the program by default. There are a couple methods to doing this on the forums and it would make the Windows app seem less alien to the environment. I think the two methods are using winecnf to set up a .msstyle file as the look for Windows program and another thread makes it possible to simply pick a colour skin for wine. I'd look them up for you, but I need to get back to my studies and really shouldn't have logged into the forums in the first place. 

Anyway, blessings on your work.

Thanks for you suggestions. I did try to skin the Virtual Rosary, but I ran into trouble with that once I began to incorporate it into the LiveCD since there is not a user directory during the build. I will of course continue to see if I can find a way to polish things up a bit. :)

God Bless, Jereme

---

### Post by doobit on 2006-12-12
> **mhancoc7 said:**
> Thanks for your kind words and for your feedback.

I believe the problem that you are having with the Dansguardian script on Xubuntu may just be that you need gedit installed.

Let me know if that fixes it.
God Bless, Jereme

Ah, OK, that makes sense. That's true that gedit is not in Xubuntu. I'll give that a try.

---

### Post by finferflu on 2006-12-12
> **mhancoc7 said:**
> 
I appreciate your concerns. I do anticipate a possible backlash. However, one of the goals of Ubuntu CE is to be a resource for both Protestants and Catholics. Some Catholics might be offended that the KJV is installed by default as well. I think that it would be wrong to make it seem as if the "Catholic programs" are not ok to include by default. I think the same about the "Protestant programs" as well.

I hope that makes since.

God Bless, Jereme

Well, I did not mean that the Protestant programs should have been the default ones, but, as already pointed out, it would be very useful to have a prompt during the installation asking what to install, i.e. Protestant or Catholic software (sorry for the very laaaaarge generalisation). I just singled out Protestants because I know their mainstream line of thought, but I don't know much about Catholics. 

Thinking about it, it's very difficult to define the word "Christian" without offending anyone. :-k

---

### Post by TheMono on 2006-12-12
I do not agree with prompting - No matter how many options you give, you will always forget somebody.

On another note, it always amazes me how much progress gets made on Ubuntu CE, given, as far as I know, that only one man is behind it.

It is great work, well done.

I have to admit though, that I am not a fan of the XP styling. If you are going to do it that style though, you may be better to remove the top GNOME panel completely... It doesn´t appear to be very functional in your layout. And I do understand why you are doing

---

### Post by finferflu on 2006-12-12
> **TheMono said:**
> 
I have to admit though, that I am not a fan of the XP styling. If you are going to do it that style though, you may be better to remove the top GNOME panel completely... It doesn´t appear to be very functional in your layout. And I do understand why you are doing

I agree, it would look better without the top panel, given your layout...

---

### Post by mhancoc7 on 2006-12-12
> **finferflu said:**
> Thinking about it, it's very difficult to define the word "Christian" without offending anyone. :-k

You hit the nail on the head. No matter what I do with Ubuntu CE someone will get upset. If it is not a Protestant/Catholic thing it would be Proprietary/Open-Source one. I do appreciate your concerns and I will of course take them into consideration.

> **TheMono said:**
> I do not agree with prompting - No matter how many options you give, you will always forget somebody.

Exactly! :)

> **TheMono said:**
>  On another note, it always amazes me how much progress gets made on Ubuntu CE, given, as far as I know, that only one man is behind it.

Well, thanks! I appreciate that, but the progress is fueled from user requests and the support the forums and of course all the team members. One thing that does make things move fast is the fact that I am able to make decisions quickly since the project is very "centralized". 

> **TheMono said:**
>  It is great work, well done.

Thanks again!

> **TheMono said:**
>  I have to admit though, that I am not a fan of the XP styling. If you are going to do it that style though, you may be better to remove the top GNOME panel completely... It doesn´t appear to be very functional in your layout. And I do understand why you are doing

Yeah, I know that this will probably not be the most popular move among Linux veterans. I might consider losing the top panel, but I think it servers a great purpose in having a place for those extras like the Workspace Switcher, Desk Bar, and the Trash Can. This is a very similiar setup to what I use on my own desktop. I like the fusion of Linux and XP styles. I don't like Windows, but I do like the Start button. So I figure why "throw the baby out with the bath water". :)

Thanks, Jereme

---

### Post by mhancoc7 on 2006-12-12
> **finferflu said:**
> I agree, it would look better without the top panel, given your layout...

Yeah, I am going to take another look at this. Nothing is set in stone yet so any suggestions will be welcomed.

Jereme

---

### Post by dakotadare2b on 2006-12-12
I like the idea to make the look of Ubuntu more "inviting" for a Windows user, as most churches use Windows as their main os. It would help the end-user to connect with Ubuntu. I talked to my pastor about Ubuntu, and his eyes just started to glaze over. I have more work to do on this.;) 

I have had mixed feelings about the double panels, since moving to Ubuntu from Windows. I have found some nice uses for it, though.

I am Lutheran, and have no problems with the Virtual Rosary being part of the distro. I have enjoyed all the distinct changes done to the CE version vs. the standard Ubuntu.

I keep coming back to see what new changes are around the bend. Keep up the GREAT work, Jereme and crew!

God Bless,
Randy

---

### Post by mhancoc7 on 2006-12-12
> **dakotadare2b said:**
> I like the idea to make the look of Ubuntu more "inviting" for a Windows user, as most churches use Windows as their main os. It would help the end-user to connect with Ubuntu. I talked to my pastor about Ubuntu, and his eyes just started to glaze over. I have more work to do on this.;) 

I have had mixed feelings about the double panels, since moving to Ubuntu from Windows. I have found some nice uses for it, though.

I am Lutheran, and have no problems with the Virtual Rosary being part of the distro. I have enjoyed all the distinct changes done to the CE version vs. the standard Ubuntu.

I keep coming back to see what new changes are around the bend. Keep up the GREAT work, Jereme and crew!

God Bless,
Randy

Thanks so much for your feedback and kind words.

God Bless, Jereme

---

### Post by mysticrider92 on 2006-12-12
If only the dvd legality issues could be solved, this would be a perfect replacement for XP on the computer in the audio/video booth at the church my family and I go to. The new look will be good for the people who havn't used Linux before (along with the large amount who don't even know what Linux is).

---

### Post by finferflu on 2006-12-13
> **mysticrider92 said:**
> If only the dvd legality issues could be solved, this would be a perfect replacement for XP on the computer in the audio/video booth at the church my family and I go to. The new look will be good for the people who havn't used Linux before (along with the large amount who don't even know what Linux is).

What are those DVD legality issues you are talking about? I'm completely ignorant in this matter, I need to know :-k 

Links are welcome :)

---

### Post by doobit on 2006-12-13
Jeremy,
One good marketing technique that you could add is to put links in Bookmarks Toolbar folder of the favorites menu of Firefox for your support pages. Also you could include a favorites folder of Bible Study and other useful Christian sites, like Bible Gateway, for example.

I installed gedit on my Xubuntu CE machine and the Parental Controls menu now works.
I'll start a new thread with this for anyone interested in Xubuntu CE.

---

### Post by mhancoc7 on 2006-12-13
> **doobit said:**
> Jeremy,
One good marketing technique that you could add is to put links in Bookmarks Toolbar folder of the favorites menu of Firefox for your support pages. Also you could include a favorites folder of Bible Study and other useful Christian sites, like Bible Gateway, for example.

I installed gedit on my Xubuntu CE machine and the Parental Controls menu now works.
I'll start a new thread with this for anyone interested in Xubuntu CE.

Actually the bookmark links for Ubuntu CE are already included in Ubuntu CE. If you use the convert_me script the bookmarks will not be visible, but if you do a fresh install they will.

Glad to hear you got it working.

God Bless, Jereme

---

### Post by Darrious on 2006-12-13
I did not know that. Maybe I should do a fresh install. :)

---

### Post by mhancoc7 on 2006-12-13
> **Darrious said:**
> I did not know that. Maybe I should do a fresh install. :)

Just like with the default Ubuntu, I believe a fresh install should always be the preferred method. It ensures that you will get everything.

Jereme

---

### Post by Darrious on 2006-12-15
Then again, I like the conversion script considering I have hundreds of files that I can't delete, or I might get fired.:p

---

### Post by doobit on 2006-12-15
> **Darrious said:**
> Then again, I like the conversion script considering I have hundreds of files that I can't delete, or I might get fired.:p

You can put the links in the Bookmarks toolbar folder yourself anyway.

---

### Post by Darrious on 2006-12-15
Yes I know, that is why I just stick to the conversion script. 

Plus, I don't know what links are there.

---

### Post by HareBall on 2006-12-16
> **dakotadare2b said:**
> 
I am Lutheran, and have no problems with the Virtual Rosary being part of the distro. I have enjoyed all the distinct changes done to the CE version vs. the standard Ubuntu.

I keep coming back to see what new changes are around the bend. Keep up the GREAT work, Jereme and crew!

God Bless,
Randy
I am Non-Denominational, and I also don't have a problem with the Rosary. I think that if it is a stumbling block, you need to look at your faith. We are assaulted everyday with things much worse than this(not that I think it is bad) and we don't even bat an eye.
Also you can remove it after installation anyway.

---

### Post by finferflu on 2006-12-17
> **HareBall said:**
> I am Non-Denominational, and I also don't have a problem with the Rosary. I think that if it is a stumbling block, you need to look at your faith. We are assaulted everyday with things much worse than this(not that I think it is bad) and we don't even bat an eye.
Also you can remove it after installation anyway.

In fact, I was only referring to Protestants, let me narrow it down further, to Evangelicals, which occupy a large percentage of Protestants.

---

### Post by shane2peru on 2006-12-19
I for one could not give out the Ubuntu CE with the Rosary program on it.  I do appreciate Ubuntu CE really enjoyed the first Edition of it.  I am Baptist, and we are not Protestant, in that we didn't Protest and come out of the Catholic church, we were never a part of it.  I certainly don't want to start, a war, and do appreciate the project.  I figured it would be too good to be true.  I think by adding the program it will quickly turn to Ubuntu Catholic Edition.  There is certainly nothing wrong with that as has been pointed out.  However you are eliminating many that may use it, I'm sure you are also adding a group that will use it.  So in the end you will have to count the cost and the worth of the program.  Either way, turn people away or towards.  Please understand that I am not an enemy to Catholics, I love people, but feel very strongly about what I believe.  I do hope your efforts go well, and do succeed.  

Shane

---

### Post by HareBall on 2006-12-19
> **shane2peru said:**
> I for one could not give out the Ubuntu CE with the Rosary program on it.  I do appreciate Ubuntu CE really enjoyed the first Edition of it.  I am Baptist, and we are not Protestant, in that we didn't Protest and come out of the Catholic church, we were never a part of it.  I certainly don't want to start, a war, and do appreciate the project.  I figured it would be too good to be true.  I think by adding the program it will quickly turn to Ubuntu Catholic Edition.  There is certainly nothing wrong with that as has been pointed out.  However you are eliminating many that may use it, I'm sure you are also adding a group that will use it.  So in the end you will have to count the cost and the worth of the program.  Either way, turn people away or towards.  Please understand that I am not an enemy to Catholics, I love people, but feel very strongly about what I believe.  I do hope your efforts go well, and do succeed.  

Shane
I am also a Baptist, but from what I read, we are also a Protestant.
According to the definition from dictionary.com:
Prot·es·tant     /&#712;pr&#594;t&#601;st&#601;nt or, for 4, 6, pr&#601;&#712;t&#603;st&#601;nt/&#8211;noun
1.	any Western Christian who is not an adherent of a Catholic, Anglican, or Eastern Church. [COLOR="Red"](This pretty much says it here)[/COLOR]
2.	an adherent of any of those Christian bodies that separated from the Church of Rome during the Reformation, or of any group descended from them.
3.	(originally) any of the German princes who protested against the decision of the Diet of Speyer in 1529, which had denounced the Reformation.
4.	(lowercase) a person who protests.

---

### Post by mhancoc7 on 2006-12-20
> **shane2peru said:**
> I for one could not give out the Ubuntu CE with the Rosary program on it.  I do appreciate Ubuntu CE really enjoyed the first Edition of it.  I am Baptist, and we are not Protestant, in that we didn't Protest and come out of the Catholic church, we were never a part of it.  I certainly don't want to start, a war, and do appreciate the project.  I figured it would be too good to be true.  I think by adding the program it will quickly turn to Ubuntu Catholic Edition.  There is certainly nothing wrong with that as has been pointed out.  However you are eliminating many that may use it, I'm sure you are also adding a group that will use it.  So in the end you will have to count the cost and the worth of the program.  Either way, turn people away or towards.  Please understand that I am not an enemy to Catholics, I love people, but feel very strongly about what I believe.  I do hope your efforts go well, and do succeed.  

Shane

Well, I truly am sorry that you feel that way. I understand your position and respect it. 

I am aware that some will not like it and choose to not use it, however, I feel that it is worth including. I am not trying or planning to turn Ubuntu Christian Edition into Ubuntu Catholic Edition. I imagine there may be some Catholics who do not like the KJV Bible being included, but it is of course going to continue to be included.

I do not want to try to convince you one way or the other. I trust that you will do what is best for you and that is a good thing. I do think that the Rosary is one of the more misunderstood practices of the Catholic Church. Martin Luther himself continue to pray the Rosary even after leaving the Church. There area also so many non-Catholics that are beginning to use it as a part of their prayer life. Many of them substitute the Jesus Prayer in place of the Hail Mary. This is a completely acceptable way to pray the Rosary.

Anyway, I hope to still see you around the forum. I wish you the very best that life has to offer.

God Bless and Merry Christmas, Jereme

---

### Post by shane2peru on 2006-12-20
> **mhancoc7 said:**
> Well, I truly am sorry that you feel that way. I understand your position and respect it. 

I am aware that some will not like it and choose to not use it, however, I feel that it is worth including. I am not trying or planning to turn Ubuntu Christian Edition into Ubuntu Catholic Edition. I imagine there may be some Catholics who do not like the KJV Bible being included, but it is of course going to continue to be included.

I do not want to try to convince you one way or the other. I trust that you will do what is best for you and that is a good thing. I do think that the Rosary is one of the more misunderstood practices of the Catholic Church. Martin Luther himself continue to pray the Rosary even after leaving the Church. There area also so many non-Catholics that are beginning to use it as a part of their prayer life. Many of them substitute the Jesus Prayer in place of the Hail Mary. This is a completely acceptable way to pray the Rosary.

Anyway, I hope to still see you around the forum. I wish you the very best that life has to offer.

God Bless and Merry Christmas, Jereme

Jereme,

   I will certainly be around the forums, I do love Linux, and am especially keen of Ubuntu.  And certainly will help in any way that I can. I know there are many good people using Ubuntu CE.  I'll refrain from an comments on the rest to keep from changing the thread into a religious thread, just wanted to put in my 'vote'.  Listened to you on the pod cast, I think you did a good job!

Merry Christmas!
Shane

Ps.  Oh, and I do appreciate all the work you have put into getting Dan's guardian functional, and easy to setup, that I certainly can and will present to others!

---

### Post by montgoej on 2006-12-22
> **shane2peru said:**
> I for one could not give out the Ubuntu CE with the Rosary program on it.  I do appreciate Ubuntu CE really enjoyed the first Edition of it.  I am Baptist, and we are not Protestant, in that we didn't Protest and come out of the Catholic church, we were never a part of it.  I certainly don't want to start, a war, and do appreciate the project.  I figured it would be too good to be true.  I think by adding the program it will quickly turn to Ubuntu Catholic Edition.  There is certainly nothing wrong with that as has been pointed out.  However you are eliminating many that may use it, I'm sure you are also adding a group that will use it.  So in the end you will have to count the cost and the worth of the program.  Either way, turn people away or towards.  Please understand that I am not an enemy to Catholics, I love people, but feel very strongly about what I believe.  I do hope your efforts go well, and do succeed.  

Shane

You could always just use Reconstructor or something to take the Rosary program out of the ISO itself, since that's one of the things makes Free Software so awesome, where if you don't like something, you can change it.  I am Baptist myself and don't see a problem with it being in there, but suit yourself, it's your call to make.

God bless,
Jordan Montgomery

---

### Post by shane2peru on 2006-12-22
That is a thought,  I don't know how much work that would be, and if it would be worth it to me.  That would be similar to starting yet another project, and I'm not quite that up to the challenge. I'm a computer user not a computer programmer.  I also have limited time as I'm a missionary in Peru.  That is my main reasoning why I couldn't give it out here in Peru, people here are converting from Catholicism.  Including anything of that nature would not be a help for my cause.  Plus the circles I run, that just would not fly well.  I again am biting my tongue to keep from converting this thread into a friendly religious debate. :D  Thanks for the thought though.  I do appreciate it, and will possibly consider it.

Merry Christmas,
Shane

---

### Post by serlex on 2006-12-22
im sorry if it has been discussed before, but are you serious with the "start" button? please noooo

---

### Post by dakotadare2b on 2006-12-22
> **serlex said:**
> im sorry if it has been discussed before, but are you serious with the "start" button? please noooo

What about renaming the "Start" button to "Begin"? Or even something Biblical, like "Genesis"? Just a couple quick thoughts.

Merry Christmas,
Randy

---

### Post by finferflu on 2006-12-22
> **shane2peru said:**
> I also have limited time as I'm a missionary in Peru.  That is my main reasoning why I couldn't give it out here in Peru, people here are converting from Catholicism.  Including anything of that nature would not be a help for my cause.  Plus the circles I run, that just would not fly well. 

Now that's funny! You're asking a Catholic developer to build an OS without Catholic influences, in order to convert people from Catholicism!!! :mrgreen:

---

### Post by shane2peru on 2006-12-22
> **finferflu said:**
> Now that's funny! You're asking a Catholic developer to build an OS without Catholic influences, in order to convert people from Catholicism!!! :mrgreen:

Well, I didn't really know it at first.  I must have missed that memo, because, I wouldn't ask that.   It is rather funny and ironic how it turned out.  I realized after I listened to the podcast.  Oh, well.  :D 

Shane

---

### Post by mhancoc7 on 2006-12-22
> **finferflu said:**
> Now that's funny! You're asking a Catholic developer to build an OS without Catholic influences, in order to convert people from Catholicism!!! :mrgreen:

Well, I am not Catholic. I am in the process of becoming Catholic, but ironic none the less. :)

> **shane2peru said:**
> Well, I didn't really know it at first.  I must have missed that memo, because, I wouldn't ask that.   It is rather funny and ironic how it turned out.  I realized after I listened to the podcast.  Oh, well.  :D 

Shane

No worries. ;)

I should mention that Ubuntu CE v1.5x (Dapper) will not include the Virtual Rosary program. So that may be an option for you to be able to give out the cds. 

I am seriously thinking about whether or not to include the Virtual Rosary program. I may consider leaving it out and releasing it as an "add on". I don't want Ubuntu CE to make anyone feel excluded. I know that I will never be able to truly accomplish that, but it is my goal regardless.

God Bless, Jereme

---

### Post by shane2peru on 2006-12-22
> **mhancoc7 said:**
> 
I should mention that Ubuntu CE v1.5x (Dapper) will not include the Virtual Rosary program. So that may be an option for you to be able to give out the cds. 

I am seriously thinking about whether or not to include the Virtual Rosary program. I may consider leaving it out and releasing it as an "add on". I don't want Ubuntu CE to make anyone feel excluded. I know that I will never be able to truly accomplish that, but it is my goal regardless.

God Bless, Jereme


Hey, Good point!  Thanks, I like that better than trying to master my own.  Dapper is very decent, I didn't like it as much for some reason, but Edgy seems to be very good for my computer.  None the less, Dapper, would probably be a better thing to distribute as it is LTS.  

Merry Christmas,
Shane

---

### Post by mhancoc7 on 2006-12-22
> **serlex said:**
> im sorry if it has been discussed before, but are you serious with the "start" button? please noooo

Yes, I am serious about it. One of the main goals of Ubuntu CE is to introduce Linux to computer users who may have never heard of Linux. Having a familiar look and feel can help users feel more "at home".

Jereme

---

### Post by shane2peru on 2006-12-23
> **mhancoc7 said:**
> Yes, I am serious about it. One of the main goals of Ubuntu CE is to introduce Linux to computer users who may have never heard of Linux. Having a familiar look and feel can help users feel more "at home".

Jereme

I understand that Linux purists would not like that.  That is the reason we are not targeting Linux Purists.  Most likely anyone that has used Linux for a while will know how to change it back.  However I do agree that this will help new users get acquainted more quickly with linux.  That is one of the things that initially led me to KDE.  It was more windows like.  I now prefer Gnome as it just runs smoother.  It isn't as pretty as KDE, and doesn't have all the toys of KDE, but they are really making it better.  You can see in the screen shot I moved my menu to the Bottom.  Hey, old habits are hard to break, and after using Windows for 15 years (growing up on windows) you really get used to that menu down there.  That may be an alternative to that actual Start button.  Either way, I think it will be helpful in for newbies.  

Shane

---

### Post by Kossilar on 2007-01-11
I think you're crazy for coming up with the concept of a virtual rosary. 

But God bless you most abundantly all the same.

---

### Post by mhancoc7 on 2007-01-13
> **Kossilar said:**
> I think you're crazy for coming up with the concept of a virtual rosary. 

But God bless you most abundantly all the same.

Well, I did not come up with the Virtual Rosary. I am just including it.

Thanks for your kind words of support.

God Bless, Jereme

---

### Post by vilto on 2007-03-02
hey mhancoc7's just saw this ubuntu CE...... and i suggested some of my friends....they really liked it......great work thr....

but i somehow feel the the gnome panel look is better than tht look like the windows.......just make it some trasparent and add some color..........i think it would be better :)

here is my screen shot
[http://img109.imageshack.us/my.php?image=screenshotqc5.png](http://img109.imageshack.us/my.php?image=screenshotqc5.png)

great work thr dude

and plz check ur private message.:)

---

### Post by mhancoc7 on 2007-03-02
> **vilto said:**
> hey mhancoc7's just saw this ubuntu CE...... and i suggested some of my friends....they really liked it......great work thr....

but i somehow feel the the gnome panel look is better than tht look like the windows.......just make it some trasparent and add some color..........i think it would be better :)

here is my screen shot
[http://img109.imageshack.us/my.php?image=screenshotqc5.png](http://img109.imageshack.us/my.php?image=screenshotqc5.png)

great work thr dude

and plz check ur private message.:)

Thanks for your interest into Ubuntu CE. I like the panel in your screenshot. The great thing about Linux is how customizable it is. I chose the Windows-ish look for Ubuntu CE 2.x because I believe it makes for an easier transition from Windows. Since a lot of Christians/Churches use Windows this made sense to me.

I will check my PM.

God Bless, Jereme

---

