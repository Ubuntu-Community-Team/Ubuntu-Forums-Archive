---
title: "Nautilus shows 'me' as owner instead of user name"
date: 2012-07-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MacUntu on 2012-07-20
The new Nautilus no longer shows the user name as owner of a file, but instead displays 'me':

[IMG]http://img.xrmb2.net/images/500792.png[/IMG]

If this bothers you, leave a comment explaining why you think this is a defect/bug of Nautilus. **Please don't start discussions in the bug report**, this is only to collect info why you think that this is something that needs fixing.

[https://bugzilla.gnome.org/show_bug.cgi?id=680282](https://bugzilla.gnome.org/show_bug.cgi?id=680282)

---

### Post by zombifier25 on 2012-07-20
What if there is a user named "me"? Isn't GNOME done with dumbing down the UI? Dangit.

---

### Post by pressureman on 2012-07-20
Wow. GNOME really needs to hire a usability expert to veto some of these stupid ideas.

Luna is looking better by the day.

---

### Post by QIII on 2012-07-20
"me" is illogical.

It is the first person and implies that the machine, rather than the user, is the owner of the process or file.

"Hey, user!  I'm in charge of this, so get lost!"

"you" might be workable, since the machine would be reporting to you, as the user, that you own the process or file.

Still, the username has long been the convention and is not ambiguous.

---

### Post by ventrical on 2012-07-20
"me , my and I".

"My Computer" , MyFiles, MyNautilus.


 If I were a Scottsman (say Scotty on Star Trek) I might say .. "I can't get me computer to reboot captain"!

:)

But you're right. It's gotta get fixed.

---

### Post by ventrical on 2012-07-20
"me" is a pronoun. <name of person here> is a proper noun. This is a matter of assignment.

 I did decide to file a bug on this, all kidding aside.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1027216](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1027216)

---

### Post by Morbius1 on 2012-07-20
> **pressureman said:**
> Wow. GNOME really needs to hire a usability expert to veto some of these stupid ideas.

This all fits with the Gnome Central Commands guidelines: [http://developer.gnome.org/hig-book/stable/principles-people.html.en](http://developer.gnome.org/hig-book/stable/principles-people.html.en)
> Remember that the purpose of any  software application is to enable some group of people to accomplish a  specific set of tasks.  So, the first things to establish when designing  your application are:
 
[LIST=1]
[*]who your users are
[*]what you want to enable them to do
[/LIST]

Is not "me" a user?

Item 2 is kind of interesting isn't it? One would think that it should read: "what the users told you they want it to do" Software development in the real world would get a whole lot simpler if the development team told the users: this is what you need.

---

### Post by ventrical on 2012-07-20
"me" is ambiguous. Might as well then call it "I".

"
*Me* is used in many constructions where strict grammarians prescribe *I.* This usage is not so much ungrammatical as indicative of the shrinking range of the nominative form: *me* began to replace *I* sometime around the 16th century largely because of the pressure of word order. *I* is now chiefly used as the subject of an immediately following verb. *Me* occurs in every other position: absolutely <who, *me*?>, emphatically <*me* too>, and after prepositions, conjunctions, and verbs, including *be* <come with *me*> <you're as big as *me*> <it's *me*>. Almost all usage books recognize the legitimacy of *me* in these positions, especially in speech; some recommend *I* in formal and especially written contexts after *be* and after *as* and *than* when the first term of the comparison is the subject of a verb.
[B]"
[/B]

---

### Post by QIII on 2012-07-20
"me" is ambiguous because as the "person speaking" the machine is identifying itself as the owner.

---

### Post by QIII on 2012-07-20
[QUOTE=Morbius]Software development in the real world would get a whole lot simpler if the development team told the users: this is what you need.[/QUOTE]

Easier, perhaps.  But dictatorial.  :)

Item 2 is definitely an interesting take.

Software development should be directed by the users' expressed needs.  Developers should not drive how the users go about their business.

Otherwise developers go to work for Microsoft.  ;)


(I don't gripe about Microsoft's products in general.  And their developers are certainly dedicated and skilled. Just don't care for Microsoft's business practices.)

---

### Post by MG&amp;TL on 2012-07-20
Aside from the problem with other users named 'me', I agree with this. 

It's more obvious for users who've had their account setup for them; it also saves screen space for more important data - how often is it that you see anybody else's files but your own? When you do, you want to know about it, and the large username should make that obvious.

---

### Post by QIII on 2012-07-20
In which case "you" might be better.

The machine would be saying "Hey, user, this file belongs to you."

---

### Post by Morbius1 on 2012-07-20
In reality though a phone, tablet, or TV are all single user systems so there really is no point any longer to show owner or group. Come to think of it I'm not sure we need a file manager any longer. 

Sorry folks, I can no longer take Gnome seriously since they either aren't taking it seriously themselves or they are designing for a device I have no intention of using Gnome with. I just hope this doesn't permeate into XFCE.

---

### Post by ventrical on 2012-07-20
Boy oh boy .. yeah... like  "you are here" as oppsossed to "me are here" or "I am here". It is purely a schemantical problem. User_name  is logically  the correct assignment for the flag to point to.

By using "me" then your iPad or tablet becomes a personal vanity, not a personal computer. In a conceptual sense, making reference to a Proper Noun (like a user_name) distinguishes a device as a personal computer. Using "me" could then be just about anybody on the planet. The PC is then depersonalized and is generally assigned to everyone because we are all "mes" and so all the "mes" can claim ownership.

  Whatever the case .. it is really bad programming to let this one slide (IMO)

---

### Post by MG&amp;TL on 2012-07-20
> **QIII said:**
> In which case "you" might be better.

The machine would be saying "Hey, user, this file belongs to you."

If I was writing with a pencil, would I write 'this writing belongs to you'? No, I'd write 'this writing belongs to me'.  In my mind, it's the same with a (bigger) tool. Those files are mine, and I made them. So they belong to me. 

But it's a matter of taste. Flickr does something similiar where the author field is "YOU!".

---

### Post by QIII on 2012-07-20
Wrong analogy, I think.

Say Joe had a bunch of stuff on a table.  Joe wanted to express who owned the items. So Joe made some cards to put in front of the items to show who they belonged to.   For some items, he wrote "root" on the card.  For the others, he wrote "me".

As you sit in your computer chair looking at the cards Joe has written, how do you interpret the ownership of the items labeled "me"?

Are they yours or Joe's?

Now change your computer's name to "Joe".  How do you interpret the cards?

---

### Post by MG&amp;TL on 2012-07-20
> **QIII said:**
> Wrong analogy, I think.

Say Joe had a bunch of stuff on a table.  Joe wanted to express who owned the items. So Joe made some cards to put in front of the items to show who they belonged to.   For some items, he wrote "root" on the card.  For the others, he wrote "me".

As you sit in your computer chair looking at the cards Joe has written, how do you interpret the ownership of the items labeled "me"?

Are they yours or Joe's?

Now change "Joe" to your computer's name.  How do you interpret the cards?

Okay, but that's just one way of looking at it. And from my point of view, the table would be the computer.

Another metaphor might be a load of clothes on a table. They've all got labels in, and they all need picking up by their respective owners. As the owners pass by the table and pick up their clothes, they look through the labels. 

If their eyes (their file manager! :lol: ) see their name, their brain translates it to 'me', or 'mine', without too much thought on their part. Another person might pass by, but the clothes they see as 'mine' are actually theirs.

But hey, this is nitpicking. I like it, myself. Have fun convincing the GNOME devs. :D

---

### Post by mc4man on 2012-07-20
Because this is an informative display I'd just use "you are" instead of "me'. Same point, can't be a username

---

### Post by zombifier25 on 2012-07-20
> **MG&TL said:**
> Aside from the problem with other users named 'me', I agree with this. 

It's more obvious for users who've had their account setup for them; it also saves screen space for more important data - how often is it that you see anybody else's files but your own? When you do, you want to know about it, and the large username should make that obvious.

I don't think users who have their accounts set up for them even NEED to know their files' ownership. And even if they do, they ain't that dumb. The freaking username is written on the top right (it's the display name, but it rarely differs from the real username anyway), and everytime they want to install something, a password box pops up asking for the current username's password, not "MY" password.

If this keeps up I'm abandoning GNOME.

---

### Post by MacUntu on 2012-07-21
Owner/group/permissions aren't displayed by default IIRC.

---

### Post by Morbius1 on 2012-07-21
So what exactly happens when you do:
```
sudo chown me /path
```

---

### Post by effenberg0x0 on 2012-07-21
Should we export ${ME}? (or ${me}, or ${Me}) :P

As long as [[ $(echo $USER) -ne "me" ]]... Then again we never worried about users named "user". There probably are some "User Smith" out there.

Now, I don't know if "Me" is a common name somewhere in the globe, but it is likely more common than people named "User". And more likely to be the two initials of some name, used as a login. I use my two initials as a login (but they are not M and E lol)...

A better idea to destroy Ubuntu: Considering we have our pic taken by the webcam during install, maybe Nautilus should display this picture instead of "me"? It would contribute more effectively to making simple file manager usage slow, borked and counterintuitive while still not helping ordinary users who not care or know what ownership/permissions are.

Regards,
Effenberg

---

### Post by Morbius1 on 2012-07-21
> **effenberg0x0 said:**
> A better idea to destroy Ubuntu: Considering we have our pic taken by the webcam during install, maybe Nautilus should display this picture instead of "me"? It would contribute more effectively to making simple file manager usage slow, borked and counterintuitive while still not helping ordinary users who not care or know what ownership/permissions are.
Well, first of all the space allocated to owner in nautilus is way too small for a picture so it will show up as a smudge to anyone over 40. And second, how on earth do I do a chown:
```
sudo chown me.png /path
```I'm sorry but I don't see that as workable solution but I like where you are heading. Anything that actually removes words would greatly improve the situation.

---

### Post by effenberg0x0 on 2012-07-21
> **Morbius1 said:**
> Well, first of all the space allocated to owner in nautilus is way too small for a picture so it will show up as a smudge to anyone over 40. And second, how on earth do I do a chmod:
```
sudo chmod me.png /path
```I'm sorry but I don't see that as workable solution but I like where you are heading. Anything that actually removes words would greatly improve the situation.

True... Maybe sound is an option? A small icon of a boombox that, onMouseOver plays the username? And why not change chown/chmod too?

Instead of chown ${USER}:${USER} ~/somefile we would just chown and speak.

$ chown ~/somefile<enter>
Please say the username...........OK! 
You said "Me"? (Y/N)y
~/somefile is now owned by Me.
$

---

### Post by Morbius1 on 2012-07-21
> **effenberg0x0 said:**
> True... Maybe sound is an option? A small icon of a boombox that, onMouseOver plays the username? And why not change chown/chmod too?

Instead of chown ${USER}:${USER} ~/somefile we would just chown and speak.

$ chown ~/somefile<enter>
Please say the username...........OK! 
You said "Me"? (Y/N)y
~/somefile is now owned by Me.
$
The hearing impaired would have a problem with that - we don't want to be discriminatory. Looks like we're stuck with me although there is still a problem with consistency. Attached below is how permissions are dealt with in the future ( [http://worldofgnome.org/nautilus-extreme-makeover/](http://worldofgnome.org/nautilus-extreme-makeover/) ). There's:

* You
* Everyone Else
* Some Other Dude ( I'm not making this up folks )

So just to be consistent "me" should be replaced by "you". 

[COLOR=Blue]*Note: I'm still trying to figure out which one of those represents "group".*[/COLOR]

---

### Post by arpanaut on 2012-07-21
Sheesh????? 
> * Some Other Dude

Now, that's really Professional!
And we want Linux to be taken seriously by business'?

I'm Appalled. Don't know if I should laugh or cry!

---

### Post by jbicha on 2012-07-21
The "User Accounts" panel in System Settings has said "My Account" since GNOME 3.0 and I don't think people complained about that in particular.

---

### Post by Morbius1 on 2012-07-21
> **jbicha said:**
> The "User Accounts" panel in System Settings has said "My Account" since GNOME 3.0 and I don't think people complained about that in particular.
You mean the replacement for the "Users and Groups" utility that we had in Gnome2 before the Gnome developers determined that we had no business messing with groups?

---

### Post by MG&amp;TL on 2012-07-21
> **Morbius1 said:**
> You mean the replacement for the "Users and Groups" utility that we had in Gnome2 before the Gnome developers determined that we had no business messing with groups?

I'll stick my neck out yet again, but I'm of the opinion that if you need to administer groups, you should probably be competent with the CLI utilities.

---

### Post by Morbius1 on 2012-07-21
That brings up another question: if the user is "me" is his group "megroup" or "mygroup". And if we change it to "you" should the group be "yourgroup".

And don't get me wrong I think the new "User Accounts" is an improvement - 50% less to worry about plus I can't tell you how may times during the day I can't remember my own user name so it's good the new utility reminds me.

---

### Post by MacUntu on 2012-07-21
Me/mine/you/yours whatever. Point is: Nautilus does not provide the requested information. To me that's unacceptable (as in "'apt-get purge' unacceptable").

---

### Post by Irihapeti on 2012-07-21
The official Mozilla version of Thunderbird has (or maybe had - they might have changed it recently) a behaviour that shows all the account-owner's emails as address to "You".

There's an addon to suppress that behaviour, and it's one of the first that I install. I have several email accounts, and it's plain confusing to see all emails as to "You", regardless of which account they were sent to.

Maybe there's some logic to that behaviour, and I imagine it's probably much the same as the logic for using "Me" in Nautilus. Interesting that it leads to completely different conclusions.

I may be less likely to have more than one login, but if I do - or if I log in as someone else for admin purposes - it's going to cause similar confusion.

It doesn't give the information, but someone else's idea of a proxy for it. Not what I want.

---

### Post by ventrical on 2012-07-21
Thunar and Dolphin file managers correctly display user_name and 'root and work exceptionally well with Unity 3D.

If Nautilus devs want to truncate functionalities  or play logic word games with buisness apps then it's a no brainer.

---

### Post by mc4man on 2012-07-21
> **Irihapeti said:**
> .

I may be less likely to have more than one login, but if I do - or if I log in as someone else for admin purposes - it's going to cause similar confusion.


It's only going to cause confusion if there is a user named "me"

The whole thing seems a bit silly on Gnome's part, a bug is filed, maybe they'll reconsider, maybe not. As far as design related bugs this has a better than usual chance of being changed. (which isn't saying much as most design bugs, whether Gnome or Ubuntu, are rejected.

maybe they should of gotten to the point..

---

### Post by Irihapeti on 2012-07-21
> **mc4man said:**
> It's only going to cause confusion if there is a user named "me"

Well, I use the initials of my real name as my username, so it's entirely possible that someone called, say, Mike Evans might want to do the same.

---

### Post by effenberg0x0 on 2012-07-22
I've been thinking about it and I think the root for such bizarre ideas is Linux desperation to compete in the single-user PC market. Most Linux players (devs, influencers, etc), specially desktop/gui people, forget about multi-user environments. Imagine browsing the folders of a public server, like a FTP, the folders of an University server, a medium/large company share, a ISP, a mail server, etc. It's absolutely common to browse systems with thousands or 10's or 100's of thousand folders/users. Eventually, someone with a "me" login will show. Of course this is just a ridiculous annoyance someone invented - it won't cause great damage anyway. But the sum of all this small things is what makes the OS increasingly less professional.

Regards,
Effenberg

---

### Post by pressureman on 2012-07-23
> **effenberg0x0 said:**
> But the sum of all this small things is what makes the OS increasingly less professional.

It's not the OS that's becoming less professional - it's GNOME.

So far I haven't seen any major "dumbing down" in the kernel or other GNU userland stuff.

---

### Post by zombifier25 on 2012-07-23
> **Irihapeti said:**
> The official Mozilla version of Thunderbird has (or maybe had - they might have changed it recently) a behaviour that shows all the account-owner's emails as address to "You".

There's an addon to suppress that behaviour, and it's one of the first that I install. I have several email accounts, and it's plain confusing to see all emails as to "You", regardless of which account they were sent to.

Maybe there's some logic to that behaviour, and I imagine it's probably much the same as the logic for using "Me" in Nautilus. Interesting that it leads to completely different conclusions.

I may be less likely to have more than one login, but if I do - or if I log in as someone else for admin purposes - it's going to cause similar confusion.

It doesn't give the information, but someone else's idea of a proxy for it. Not what I want.

Thunderbird is free to show your email address as "you", because there is no way you can have an email address named "you". But any users can have their username named "me", which could be a security issue.

The problem with this approach is technical.

---

### Post by effenberg0x0 on 2012-07-24
> **pressureman said:**
> It's not the OS that's becoming less professional - it's GNOME.

So far I haven't seen any major "dumbing down" in the kernel or other GNU userland stuff.


I agree: For me, for you, it's Gnome of course. But for the ordinary user, it's all Ubuntu. People who are not on IT and have no experience or interest in development and Linux see Ubuntu as a whole OS. Just as they see MacOS, Windows, etc. Nonetheless, you're absolutely correct.

Regards,
Effenberg

---

### Post by pressureman on 2012-07-24
> **effenberg0x0 said:**
> I agree: For me, for you, it's Gnome of course. But for the ordinary user, it's all Ubuntu. People who are not on IT and have no experience or interest in development and Linux see Ubuntu as a whole OS. Just as they see MacOS, Windows, etc. Nonetheless, you're absolutely correct.

The sad part is, if the rest of the open source ecosphere isn't drinking this idiotic Kool-Aid, where the heck are GNOME taking their lead from? What is driving this perpetual dumbing down of the interface?

Kids grow up with PCs, smartphones and tablets. The general population should be becoming MORE tech savvy with each generation, not less. Why does GNOME feel the need to oversimplify things? I'm in favour of user-friendliness, but not at the expense of functionality.

---

### Post by screaminj3sus on 2012-07-24
This is just one of the many things wrong with the new version of nautilus. They keep making ridiculous changes and/or ripping out features.

---

### Post by ventrical on 2012-07-24
I tried an experiment on one particular install and chose <lock version> from synaptic, then, updated, and now Nautilus is not in the Unity dash.  Doesn't matter as I can always use <dolphin> or <thunar> (or many others).

---

### Post by Morbius1 on 2012-07-24
If we are going to start installing things like Thunar, leafpad, and gnome-system-tools would it be impertinent of me to suggest we walk towards the light instead of shunning it: [http://xubuntu.org/news/quantalalpha2/](http://xubuntu.org/news/quantalalpha2/)

---

### Post by pressureman on 2012-07-24
> **Morbius1 said:**
> If we are going to start installing things like Thunar, leafpad, and gnome-system-tools would it be impertinent of me to suggest we walk towards the light instead of shunning it: [http://xubuntu.org/news/quantalalpha2/](http://xubuntu.org/news/quantalalpha2/)

I would think that for people who like GNOME Shell, but perhaps just take issue with Nautilus and a few other apps, Elementary OS might be an interesting alternative, especially the upcoming Luna version.

[http://elementaryos.org/journal/when-its-ready](http://elementaryos.org/journal/when-its-ready)

---

### Post by ventrical on 2012-07-24
> **Morbius1 said:**
> If we are going to start installing things like Thunar, leafpad, and gnome-system-tools would it be impertinent of me to suggest we walk towards the light instead of shunning it: [http://xubuntu.org/news/quantalalpha2/](http://xubuntu.org/news/quantalalpha2/)


 I have Kubuntu, Xubuntu and Lubuntu installs and they all work great (with their designated file_managers). I just like to experiment.  Thats one of the great things about Linux/Ubuntu. I also like the Unity desktop , so, when I am in disagreement with  the way a dev may be handling a certain part of the Unity package (Nautilus) then I am going to start looking for other alternatives. There is just too much downtime involved in  trying to pursuade a developer to follow a certain standard (ie; user_name instead of 'me'). It is important because I like to  create multiple users so that I can enable a back-door when I have  a major crash  while beta testing and so knowing what user_name  I am using under a particular install only make sense.

Kubuntu, Xubuntu and Lubuntu DEs are all great and each have their own caveat but I  really like Unity desktop because of my eyes - meaning to say I can navigate  more freely because of less eyesight strain.

 However if this trend with Nautilus continues to digress then I am perfectly comfortable running Kubuntu. If this 'me' concept happens to crossover even to the other variants then there will always be some other program that will properly represent designated user_name and root.

---

### Post by mc4man on 2012-07-24
> **ventrical said:**
> so knowing what user_name  I am using under a particular install only make sense.
 
You actually use file permissions in nautilus in list view to remind/inform you of what user you're logged in as??

---

### Post by ventrical on 2012-07-24
> **mc4man said:**
> You actually use file permissions in nautilus in list view to remind/inform you of what user you're logged in as??

Actually, no. But my point was to follow the greater good of continuity in the rest of the components and apps. One example is System Monitor. It correctly reports the user_name when pressing the system tab. So then the devs can also do the same there. Just use "me" instead of user_name.  If they are going to truncate Nautilus file manager, why not truncate all managers?

 I speculate the reason they do not use "me" in system monitor is because  that tool represents the 'system' and you can't call the 'system' "me" because it's not! It represents the end_user. The same should follow with Nautilus. It reports the structure of the file_system, not the 'me' operating the file_system.

---

### Post by Mr. Picklesworth on 2012-07-25
> **ventrical said:**
> Actually, no. But my point was to follow the greater good of continuity in the rest of the components and apps. One example is System Monitor. It correctly reports the user_name when pressing the system tab. So then the devs can also do the same there. Just use "me" instead of user_name.  If they are going to truncate Nautilus file manager, why not truncate all managers?

As far as I am aware, System Monitor does not tell you your user name. It says the hostname, which could be anything.

---

### Post by ventrical on 2012-07-25
> **Mr. Picklesworth said:**
> As far as I am aware, System Monitor does not tell you your user name. It says the hostname, which could be anything.


I think you are right.   My mistake.  But  my point is (as suggested by another user) that  "me" is illogical.

---

### Post by ventrical on 2012-07-25
I hope this does not sound too frivolous but , logging into Guest Session should designate "you" instead of me.  My argument then is if nautilus/unity devs wish to use tablet logic and turn desktops into executive toy playthings then it would only be fair to do it across the board globally.

---

### Post by ventrical on 2012-07-25
pic

---

### Post by xebian on 2012-07-25
> **Mr. Picklesworth said:**
> As far as I am aware, System Monitor does not tell you your user name. It says the hostname, which could be anything.

You are just looking at one page.  Look in the 'Processes' tab.

Anyway this is just 'much ado about nothing'.

---

### Post by Morbius1 on 2012-07-25
> **ventrical said:**
> I think you are right.   My mistake.  But  my point is (as suggested by another user) that  "me" is illogical.
Depends on where you look. If you look at the process tab the user is specified and if it says "me" one would think that means root.

---

### Post by MacUntu on 2012-08-14
> Use Me instead of me to differentiate from any usernames

Trolls.

---

### Post by MacUntu on 2012-08-15
```
--- a/libnautilus-private/nautilus-file.c	2012-08-15 08:44:28.000000000 +0200
+++ b/libnautilus-private/nautilus-file.c	2012-08-15 08:43:51.046763375 +0200
@@ -5700,10 +5700,7 @@
 		return NULL;
 	}
 
-	if (file->details->uid == getuid ()) {
-		/* Translators: "me" is used to indicate the file is owned by me (the current user) */
-		user_name = g_strdup (_("me"));
-	} else if (file->details->owner_real == NULL) {
+	if (file->details->owner_real == NULL) {
 		user_name = g_strdup (eel_ref_str_peek (file->details->owner));
 	} else if (file->details->owner == NULL) {
 		user_name = g_strdup (eel_ref_str_peek (file->details->owner_real));
```

Or in the future:

```
--- a/libnautilus-private/nautilus-file.c	2012-08-15 08:44:28.000000000 +0200
+++ b/libnautilus-private/nautilus-file.c	2012-08-15 08:43:51.046763375 +0200
@@ -5700,10 +5700,7 @@
 		return NULL;
 	}
 
-	if (file->details->uid == getuid ()) {
-		/* Translators: "Me" is used to indicate the file is owned by me (the current user) */
-		user_name = g_strdup (_("Me"));
-	} else if (file->details->owner_real == NULL) {
+	if (file->details->owner_real == NULL) {
 		user_name = g_strdup (eel_ref_str_peek (file->details->owner));
 	} else if (file->details->owner == NULL) {
 		user_name = g_strdup (eel_ref_str_peek (file->details->owner_real));
```

---

