---
title: "Ubuntu &quot;Friendliness&quot; team"
date: 2009-04-07
forum: Ubuntu Brainstorm
---

### Post by spandanj on 2009-04-07
Hi,

Since we have several teams focusing on important aspects Ubuntu OS, I think we should also have a Ubuntu Friendliness that would focus on making the user experience Easy and Simple by designing proper GUI for various OS-features or help 3rd-party softwares in doing so if requested.

1) [COLOR="RoyalBlue"]***With the help of and co-ordinating with the Art team and the OS developer team***[/COLOR], the goal of the Friendliness team would be to come up with the BEST GUI for whatever OS-integrated program/feature or help a 3rd party software to come up with a simple and effective GUI designed made in GUI to make the USER EXPERIENCE easiest.

2) In order to do so, they could come up with a [COLOR="RoyalBlue"]**Friendliness Guidelines that ANY programmer out there can use to design their own GTK GUIs**[/COLOR] if they are interested. This would bring a consistency to GUI -- something that Apple has achieved remarkably well.

3) Anyone who is interested in making the user experience easy should be allowed to join this team.


I think this team would play a very important role in making UBUNTU User-friendly. Having such a team would automatically declare a commitment to the goal of Ubuntu ---- Linux for human beings. 

What are your thoughts?

---

### Post by spaceboy909 on 2009-04-07
An excellent idea, and one I've been mulling over for about the last  2 years or so when I first tried Ubuntu.

I have sampled different distros going back to 1999, and have always gone back to Windows.  One of the reasons being that the Linux desktop just isn't user-friendly enough.  Simply having a similar concept and layout from a distance isn't enough.

I've actually been fantasizing about getting a standards organization off the ground, one which seems similar to what you are talking about, although my idea would have it detached from Ubuntu, and equally accessible to all distros and developers.

I'm really only just now beginning to learn about development myself, so I'm really not in any position to get something off the ground myself.  I was just going to draw up the general idea (white paper, I guess) along with an initial set of standards to get the discussion off the ground, and then post it on a blog, and see what kind of attention it attracts.

But that isn't finished, and since I just happened to land on your post, I'll go ahead and post what I have so far, and hopefully it will generate some excitement.

Standby.........  :)

---

### Post by spaceboy909 on 2009-04-07
Well, I don't have as much done on it as I thought, so I'm going to work on it some more tonight and post it as soon as I'm done.

---

### Post by benj1 on 2009-04-07
first i don't think the idea is too bad, will this be an art or programming thing?
second i really don't like the name friendliness team, sounds like they may think its a good idea to introduce a 'friendly', 'helpful' paperclip to the desktop or something worse.

---

### Post by Stupendoussteve on 2009-04-07
Something similar already exists through Gnome itself with the Gnome Usability project ([http://live.gnome.org/UsabilityProject](http://live.gnome.org/UsabilityProject)). It includes guidelines to help developers make applications that integrate well.

May at least be a starting point, if it isn't a duplication of effort.

---

### Post by spaceboy909 on 2009-04-07
> **benj1 said:**
> first i don't think the idea is too bad, will this be an art or programming thing?
second i really don't like the name friendliness team, sounds like they may think its a good idea to introduce a 'friendly', 'helpful' paperclip to the desktop or something worse.

haha  :D  I think I recall that dancing paperclip somewhere.......

> **Stupendoussteve said:**
> Something similar already exists through Gnome itself with the Gnome Usability project ([http://live.gnome.org/UsabilityProject](http://live.gnome.org/UsabilityProject)). It includes guidelines to help developers make applications that integrate well.

May at least be a starting point, if it isn't a duplication of effort.
I'll check that out.  That may be sufficient, or maybe not.  As everything is voluntary, essentially, the real question is, how do we increase the pace of what we're already doing on the desktop?

The progress is just too slow.  Some believe that Linux does not ever need to compete on the desktop.  They are content with what it is.  Others, like myself, believe that Linux absolutely must begin gaining rapid market share in the desktop arena, for so many reasons.

To do that, we have got to ring a big fat bell for desktop developers and sound a sense of urgency..........which, honestly, from a user's perspective, just doesn't seem to be out there.

---

### Post by spaceboy909 on 2009-04-07
After going back over my list, it probably will be the case that having the organization manually review and classify various apps would be insanely time consuming, and would either require incredibly complex standards and/or widely varying interpretations!  (I love shooting down my own ideas! :(  )  

But...... the next best thing would simply be to create the classification standards, and allow the developers to use them as guidelines.  They could then optionally claim that their application meets a given standard, and promote it as such.  (I will check out the Gnome link posted earlier.)

None the less, as I put so much thought into it, I'm going to post what I had finished just as food for thought, and maybe something good will come from it.

---

### Post by spaceboy909 on 2009-04-07
[I]** I'm posting this for brainstorming purposes.  I no longer believe that an active  classification system would be feasible, but the standards are still worthwhile.
[/I]
**Desktop Standards**

**Overall objective**:

This proposed standards organization would work toward dramatically improving the 'mass-market' Linux desktop GUIs so as to increase user friendliness.  This work would be structured in such a way as to rapidly increase the rate at which:

* new users switch to Linux
* prior users switch back to Linux

It of course would also strive to ensure that the majority of users who try Linux stay with it.

**Target Audience**:

1) General end users accustomed to the common, proprietary GUI experience, and who desire the same or superior experience in Linux.

2) Desktop distributions who desire to enhance and promote GUI friendliness, thereby attracting more users.

3) Developers who desire to enhance the GUI friendliness of their applications, thereby attracting more users and support to their software.

**Purpose of Application Class Labels**

To provide an easy to understand classification label that end users can easily find, and that distro maintainers can implement into their package updating system.

An example would be in the Ubuntu-Gnome 'Add/Remove' application panel (under the applications panel menu).  When you open that application browser, you see a ratings column, where apps are rated from 1 to 5 stars.  One possible implementation for this new classification label would be to add an additional column, which would have a number from 1 to 5 (assuming for now, that there will be 5 class labels).

Users could then sort by this column, and/or filter their search results to include, for example, Class 3 apps or higher only.

By filtering on the class labels, or simply choosing the highest number, the end user would be assured that the application they are installing meets the standards they seek, and are accustomed to.

Now, a more in depth description of the classes.  For the moment, I am envisioning 5 classes, but that is open to change.


The class criteria are used to categorize the user-friendliness of an application, and the most widely accepted, common sense functions that they should have.  They are to be applied in a pass/fail fashion.  An individual class is not intended to create a multi-tiered, grading scale within itself.  Each application will be strictly judged by the criteria for each class.  A single missed criterion will yield a failing grade for that class.

It may be possible for an application to miss a single criteria in each class, thereby failing to 'rank'.  In this case, the application could simply be left out of the 'rankings' altogether, or a new class could be created for those that don't meet any of the set standards.  In this example, that would make it a Class 6, with Class 1 being a full featured GUI application, and Class 5 being a bare bones application.

CLASS 1 - Full featured GUI:

There is a lot listed here, and lots more that could go in.  Keep in mind that the idea for a Class 1 is that the developer has basically pulled out all of the stops and is going for the gold; to create the best graphical, end user experience he or she can.  So, this class *does* need to be packed full of standards that one would expect in a first rate application.

Many, if not all, of the items listed would need to be further defined, as they are open to interpretation, such as what an 'expert feature' is.  

[I]****** After going back over my list, it probably will be the case that having the organization manually review and classify various apps would be insanely time consuming, and would either require incredibly complex standards and/or widely varying interpretations!  (I love shooting down my own ideas! :(  )  

But...... the next best thing would simply be to create the classification standards, and allow the developers to use them as guidelines.  They could then optionally claim that their application meets a given standard, and promote it as such. *******[/I]

As we work our way down to Class 5 (which will take a lot more time and input), various standards will be either removed from the list, or reduced in some capacity.

At this point, I'm envisioning Class 5 as a GUI app 'in name only', so to speak.  Virtually no common or expected features in a GUI.

Now, here's the list in progress for a Class 1 GUI app.


* Must have a GUI that does not require ANY user/terminal interaction, including application startup.  A terminal may be built into the GUI as an alternative for those that prefer to use it, but the user can never be required to use a terminal.

* Must have full featured mouse support, including copy and paste and right-click menus.

* Must have basic keyboard support, and default key mapping must not interfere with other desktop operations.

* All windows and dialogue boxes, including error windows, must be re-sizable.

* Must have full drag and drop support.

* Must have a help menu, with full local/offline help available at all times.  Man/Info pages **do not** count, including copies of them into a GUI window.  

* During installation, a graphical launcher must be placed on the desktop. The exception for this is if during the installation procedure, the user is given other options.

* Must have standard/basic menu/toolbars and the general functions that go with them.

* Must have a way to edit preferences, such as in the menu toolbar, or with a window button.  The exception to having an actual preference box that pops up, is if 100% of the program's options are visible in the main window, or sub-windows as appropriate.  For the latter case of visible preferences in the window, they must be fully mouse  accessible, utilizing buttons, scroll bars, sliders, arrows, etc.

* All window buttons, switches and other mouse accessible, adjustable features must have either hard coded, text labels, or pop-up balloon descriptions.  The popular, two-step help, utilizing a toggled question mark button in the title window, after-which the user makes a subsequent click in an area of the window where he desires help, is **not** an acceptable alternative for a default installation.

It is acceptable to allow the user to toggle off the hard-text and balloons, and have the two-step question mark help as a backup.

* Auto-saving features, such as for a word processor and other appropriate apps, should be enabled by default.

* Error logging should be enabled by default, with a reasonable file size and time limit in place, for automated cleaning.  The log file should be easy to find under BOTH 'help' and 'preferences'.

* The 'Help' menu should contain the most common standard items at a minimum.  The 'About' dialogue box should contain information about the application, active website URL's, active support URL's (except when they are contained under a separate 'Help' menu item), licensing, and a button for local help as outlined earlier.

* All toolbars and items inside them should be unlocked for relocation per the user's desires.  A 'defaults' button should be available in 'preferences' to reset them, as well as at least one, autosaved, user-config selection, so that the user can switch back to their last custom configuration if they accidentally reset to defaults.

* All user customizations should be autosaved in a backup file, which can be restored later from 'preferences'.  Manual saving should be available as well.

---

### Post by spandanj on 2009-04-08
> **spaceboy909 said:**
> [I]** I'm posting this for brainstorming purposes.  I no longer believe that an active  classification system would be feasible, but the standards are still worthwhile.
[/I]
**Desktop Standards**

**Overall objective**:

This proposed standards organization would work toward dramatically improving the 'mass-market' Linux desktop GUIs so as to increase user friendliness.  This work would be structured in such a way as to rapidly increase the rate at which:

* new users switch to Linux
* prior users switch back to Linux

It of course would also strive to ensure that the majority of users who try Linux stay with it.

**Target Audience**:

1) General end users accustomed to the common, proprietary GUI experience, and who desire the same or superior experience in Linux.

2) Desktop distributions who desire to enhance and promote GUI friendliness, thereby attracting more users.

3) Developers who desire to enhance the GUI friendliness of their applications, thereby attracting more users and support to their software.

**Purpose of Application Class Labels**

To provide an easy to understand classification label that end users can easily find, and that distro maintainers can implement into their package updating system.

An example would be in the Ubuntu-Gnome 'Add/Remove' application panel (under the applications panel menu).  When you open that application browser, you see a ratings column, where apps are rated from 1 to 5 stars.  One possible implementation for this new classification label would be to add an additional column, which would have a number from 1 to 5 (assuming for now, that there will be 5 class labels).

Users could then sort by this column, and/or filter their search results to include, for example, Class 3 apps or higher only.

By filtering on the class labels, or simply choosing the highest number, the end user would be assured that the application they are installing meets the standards they seek, and are accustomed to.

Now, a more in depth description of the classes.  For the moment, I am envisioning 5 classes, but that is open to change.


The class criteria are used to categorize the user-friendliness of an application, and the most widely accepted, common sense functions that they should have.  They are to be applied in a pass/fail fashion.  An individual class is not intended to create a multi-tiered, grading scale within itself.  Each application will be strictly judged by the criteria for each class.  A single missed criterion will yield a failing grade for that class.

It may be possible for an application to miss a single criteria in each class, thereby failing to 'rank'.  In this case, the application could simply be left out of the 'rankings' altogether, or a new class could be created for those that don't meet any of the set standards.  In this example, that would make it a Class 6, with Class 1 being a full featured GUI application, and Class 5 being a bare bones application.

CLASS 1 - Full featured GUI:

There is a lot listed here, and lots more that could go in.  Keep in mind that the idea for a Class 1 is that the developer has basically pulled out all of the stops and is going for the gold; to create the best graphical, end user experience he or she can.  So, this class *does* need to be packed full of standards that one would expect in a first rate application.

Many, if not all, of the items listed would need to be further defined, as they are open to interpretation, such as what an 'expert feature' is.  

[I]****** After going back over my list, it probably will be the case that having the organization manually review and classify various apps would be insanely time consuming, and would either require incredibly complex standards and/or widely varying interpretations!  (I love shooting down my own ideas! :(  )  

But...... the next best thing would simply be to create the classification standards, and allow the developers to use them as guidelines.  They could then optionally claim that their application meets a given standard, and promote it as such. *******[/I]

As we work our way down to Class 5 (which will take a lot more time and input), various standards will be either removed from the list, or reduced in some capacity.

At this point, I'm envisioning Class 5 as a GUI app 'in name only', so to speak.  Virtually no common or expected features in a GUI.

Now, here's the list in progress for a Class 1 GUI app.


* Must have a GUI that does not require ANY user/terminal interaction, including application startup.  A terminal may be built into the GUI as an alternative for those that prefer to use it, but the user can never be required to use a terminal.

* Must have full featured mouse support, including copy and paste and right-click menus.

* Must have basic keyboard support, and default key mapping must not interfere with other desktop operations.

* All windows and dialogue boxes, including error windows, must be re-sizable.

* Must have full drag and drop support.

* Must have a help menu, with full local/offline help available at all times.  Man/Info pages **do not** count, including copies of them into a GUI window.  

* During installation, a graphical launcher must be placed on the desktop. The exception for this is if during the installation procedure, the user is given other options.

* Must have standard/basic menu/toolbars and the general functions that go with them.

* Must have a way to edit preferences, such as in the menu toolbar, or with a window button.  The exception to having an actual preference box that pops up, is if 100% of the program's options are visible in the main window, or sub-windows as appropriate.  For the latter case of visible preferences in the window, they must be fully mouse  accessible, utilizing buttons, scroll bars, sliders, arrows, etc.

* All window buttons, switches and other mouse accessible, adjustable features must have either hard coded, text labels, or pop-up balloon descriptions.  The popular, two-step help, utilizing a toggled question mark button in the title window, after-which the user makes a subsequent click in an area of the window where he desires help, is **not** an acceptable alternative for a default installation.

It is acceptable to allow the user to toggle off the hard-text and balloons, and have the two-step question mark help as a backup.

* Auto-saving features, such as for a word processor and other appropriate apps, should be enabled by default.

* Error logging should be enabled by default, with a reasonable file size and time limit in place, for automated cleaning.  The log file should be easy to find under BOTH 'help' and 'preferences'.

* The 'Help' menu should contain the most common standard items at a minimum.  The 'About' dialogue box should contain information about the application, active website URL's, active support URL's (except when they are contained under a separate 'Help' menu item), licensing, and a button for local help as outlined earlier.

* All toolbars and items inside them should be unlocked for relocation per the user's desires.  A 'defaults' button should be available in 'preferences' to reset them, as well as at least one, autosaved, user-config selection, so that the user can switch back to their last custom configuration if they accidentally reset to defaults.

* All user customizations should be autosaved in a backup file, which can be restored later from 'preferences'.  Manual saving should be available as well.

Spaceboy909,

Thanks for posting Such great ideas. I agree with you that we should, at least, come up with a GUI standard to a) rate different apps, and more importantly, b) help those developers to make their app MORE GUI oriented and thus user-friendly to normal person.

The aim of this group would be to eventually make the desktop CLI-free because that's what a "normal" as 90% of computer users out there who are novice want. Having said that it has best chances of working if it was affiliated with a single distro. In the linux world, everyone (even developers) have the freedom to make their apps as they please. However, by affiliating with a distro such a standards body would be more affective in making that distro alone GUI-oriented. It would easier to implement our idea on one distro instead of the entire linux community. Ubuntu is the best distro to implement this idea in since it already strives to be the most user-friendly.

So, if you know how, and if you can start of this team and talk with Ubuntu people, that'd be great.

Finally, on the matter of the team's name, someone was correct in pointing out that "friendliness" team sounds a bit imprecise to it's purpose. We have to call it something that an end-user as well as a developer understands exactly what it is by it's name, which, just to mention, is to help apps and their developers implement better GUIs <--that would be the goal of this team. so, call it GUE team? -- for Graphic User Experience team?


thanks

---

### Post by spandanj on 2009-04-08
[COLOR="Gray"]
Spaceboy909,

you are right. Gnome already has this--the Usability Project.


[COLOR="Black"]***Also, in terms of what needs to be done, another idea, for improving the GU experience is the process of adding repositories the PGP keys. It's just so awkward.***[/COLOR] First you have to copy paste the repo address into the "software sources". [COLOR="Black"][COLOR="Black"]**INSTEAD**[/COLOR][/COLOR], you should just be able to click the click and the GUI should, somehow, prompt the user to agree or disagree to add the repos. So simplify the copy/paste to click and agree. Secondly, to add the keys, one has to copy the entire 10 lines of key, save it in a document, then go to software source and add an authentication key. _[COLOR="Blue"]THAT is very complicated.[/COLOR]_ If no one else understands and accepts that that is a complicated process for a normal user, WE DO. ***So, this new GUE team should also come with a GUI-oriented way of authenticating the keys.....***[/COLOR]

---

### Post by smartboyathome on 2009-04-08
> **spandanj said:**
> [COLOR="Gray"][COLOR="Black"]***Also, in terms of what needs to be done, another idea, for improving the GU experience is the process of adding repositories the PGP keys. It's just so awkward.***[/COLOR] First you have to copy paste the repo address into the "software sources". [COLOR="Black"][COLOR="Black"]**INSTEAD**[/COLOR][/COLOR], you should just be able to click the click and the GUI should, somehow, prompt the user to agree or disagree to add the repos. So simplify the copy/paste to click and agree. Secondly, to add the keys, one has to copy the entire 10 lines of key, save it in a document, then go to software source and add an authentication key. _[COLOR="Blue"]THAT is very complicated.[/COLOR]_ If no one else understands and accepts that that is a complicated process for a normal user, WE DO. ***So, this new GUE team should also come with a GUI-oriented way of authenticating the keys.....***[/COLOR]

That was already available in the apturl project (which Ubuntu uses for apt:// links). Ubuntu patched it out because the devs saw it as a security risk. They don't want to help people get third party repos on Ubuntu, as that could potentially lead to a broken package or even a virus coming in, and they wouldn't be able to do anything about it.

---

### Post by linux4life88 on 2009-04-08
In my opinion it isn't something that is absolutely necessary but it could be very beneficial. I'm a huge fan of organization and I think by creating this group it would organize this part of Ubuntu distribution instead of having everything haphazardly thrown together.

---

### Post by benj1 on 2009-04-09
> **spandanj said:**
> Spaceboy909,

Thanks for posting Such great ideas. I agree with you that we should, at least, come up with a GUI standard to a) rate different apps, and more importantly, b) help those developers to make their app MORE GUI oriented and thus user-friendly to normal person.

The aim of this group would be to eventually make the desktop CLI-free because that's what a "normal" as 90% of computer users out there who are novice want. Having said that it has best chances of working if it was affiliated with a single distro. In the linux world, everyone (even developers) have the freedom to make their apps as they please. However, by affiliating with a distro such a standards body would be more affective in making that distro alone GUI-oriented. It would easier to implement our idea on one distro instead of the entire linux community. Ubuntu is the best distro to implement this idea in since it already strives to be the most user-friendly.

So, if you know how, and if you can start of this team and talk with Ubuntu people, that'd be great.

Finally, on the matter of the team's name, someone was correct in pointing out that "friendliness" team sounds a bit imprecise to it's purpose. We have to call it something that an end-user as well as a developer understands exactly what it is by it's name, which, just to mention, is to help apps and their developers implement better GUIs <--that would be the goal of this team. so, call it GUE team? -- for Graphic User Experience team?


thanks

what needs to be done from the CLI?
yes there are some things, but these arent things you need to do.
i think most people could get by knowing 2 terminal commands
'gksu nautilus'
and
'gksu gedit'
i would agree it would be worth implementing something maybe built into these two apps two apps to enable them to be used in root (yes i am aware of potential consequences), then we could truly say you don't need to use the terminal for anything.

---

### Post by Merk42 on 2009-04-09
I think something a lot of Linux/Ubuntu/GNOME etc developers don't understand is that if they want to attract new users.  They have to do usability testing to see what it is they want.  Not make something and then convince the prospective users it's what they want.

---

### Post by spaceboy909 on 2009-04-10
> **benj1 said:**
> what needs to be done from the CLI?
yes there are some things, but these arent things you need to do.
These days it's probably rare for a GUI app, but the more skimpy a GUI is (and there are still some skimpy ones out there), the more likely you are to have to resort to the console to perform a task.

---

