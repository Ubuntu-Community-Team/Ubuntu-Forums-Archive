---
title: "Ubuntu - Oversimplified?"
date: 2006-11-02
forum: The Cafe
---

### Post by jchau on 2006-11-02
I've noticed a disturbing trend in Ubuntu lately.  Ubuntu seems to be simplifying GNU/Linux to a point where moderately experienced users (or just I) will feel disabled rather than empowered.  I first started using Ubuntu back when Breezy was the current version and I liked it then because it was both easy to use (unlike some other distros, it was able to support my hardware without any problems).  However, I continued to use Ubuntu because I was able to get it to do what I wanted.  

When Dapper came along, I noticed that many options (features) have been removed.  For example, in Breezy, we were able to pick a screensaver for X and configure it (I used the phosphor screensaver with fortune messages).  After I upgraded to Dapper, these features disappeared: phosphor was no longer there and most of the options were removed.  While there might be a good reason to remove a particular screensaver from the installation, I was quite annoyed that the options were also removed.  For example, the screensavers that displayed text would no longer let me choose the text displayed and the screensavers that displayed pictures wouldn't let me pick which pictures it displayed.  Is removing "advanced" features the right way to make the OS easier to use?  While screensavers may be trivial, this is just one example to illustrate my problem.  

When Edgy came out, I decided to give that a try too and my problems grew again.  The first scary bit was being unable to tell what my computer was doing when it started (the startup screen only showed the Ubuntu logo).  Am I the only one using Ubuntu that finds not knowing what my computer is doing is more disturbing than seeing debugging messages?  This part was particularly disturbing for me since I knew that setup would need some tweaking after a significant upgrade (even when I only update the kernel, I have to recompile some third party drivers); not seeing the error messages that I knew was there kept me in the dark.  (Some of the messages don't get logged)(Anyone know how to re-enable these messages?)  Once again, this isn't the only simplification, but the one I choose to illustrate the point.  


Am I just picking the wrong flavor of GNU/Linux for myself?  Is Ubuntu going to continue to sacrifice features and options at the to become easier to use or can I expect to be able to do more with Ubuntu when Feisty comes along?

---

### Post by bruenig on 2006-11-02
If you want your informative boot again, just edit the menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
and delete the quiet and splash options from it.

---

### Post by qamelian on 2006-11-02
Many of the simplifications are not Ubuntu so much as Gnome. The screensaver thing is a perfect example. The new screensaver interface is a change in the way Gnome handles screensaver, and since Ubuntu uses Gnome, Ubuntu inherits this annoying behaviour. You'll have the same situation on any Gnome-based distro. This trend in Gnome towards hiding so much of the functionality is one of the reasons I'm considering going back to KDE. Back in the days of Gnome 1.4, I would never have even considered this move.

---

### Post by 23meg on 2006-11-02
> For example, in Breezy, we were able to pick a screensaver for X and configure it (I used the phosphor screensaver with fortune messages). After I upgraded to Dapper, these features disappearedThat wasn't Ubuntu's decision per se, but Ubuntu did follow suit with upstream when GNOME switched from xscreensaver to gnome-screensaver. I'd written more on the reasons behind that,  [here]("http://www.ubuntuforums.org/showpost.php?p=1314185&postcount=17"). I also wrote two guides to remedy it, [this]("http://www.ubuntuforums.org/showthread.php?t=195557") and [this]("http://www.ubuntuforums.org/showthread.php?t=198809"), which were utilized by many users, and a forum member even wrote a Java app to make things work more smoothly for the end user. 

> When Edgy came out, I decided to give that a try too and my problems grew again. The first scary bit was being unable to tell what my computer was doing when it started (the startup screen only showed the Ubuntu logo).
There's [a simple fix for that]("http://ubuntuforums.org/forumdisplay.php?f=170") as well, and while I do prefer seeing the messages to not seeing them, I believe not showing them as a default makes sense in a way, because they don't give any useful feedback to the non-technical user, and the more technically oriented can easily enable them.

---

### Post by autocrosser on 2006-11-02
I think that Ubuntu needs to be easy for new users---as long as the advanced users have ways to customize the OS in ways that they want.

I believe that Ubuntu is treading a fine line---and doing a very good job of it.

---

### Post by TheMono on 2006-11-02
Please, don't show the boot messages by default. Have the option, sure, but by way of metaphor, if I send someone to go pick me up a loaf of bread, I don't want a call every ten seconds saying "I'm starting the car now" "I'm taking a left" "Paying for the bread". I just want to be able to find out if something goes wrong.

---

### Post by szf on 2006-11-02
> **qamelian said:**
> This trend in Gnome towards hiding so much of the functionality is one of the reasons I'm considering going back to KDE. Ouch. Big ouch.

---

### Post by adam.tropics on 2006-11-02
Part of this is perhaps about whom Ubuntu is being targetted at. I mean on the one hand, distributing the latest and greatest will attract the techies and OS hobbyists amongst others, basically those with a certain level of technical experience. On the other hand they are trying to be a distro for everybody, and keep things as simple as possible for new users/converts. Whilst I don't think the groups are entirely mutually exclusive, there is a bit of compromise to be done in order to please as many people as possible.

Plus, as stated earlier in the thread, most options can be put back if you so wish anyway!

---

### Post by RussianVodka on 2006-11-03
> **TheMono said:**
> Please, don't show the boot messages by default. Have the option, sure, but by way of metaphor, if I send someone to go pick me up a loaf of bread, I don't want a call every ten seconds saying "I'm starting the car now" "I'm taking a left" "Paying for the bread". I just want to be able to find out if something goes wrong.

"I'm paying for the bread..."
"ERROR: NOT ENOUGH MONEY!"
"KERNEL PANIC!"

---

### Post by K.Mandla on 2006-11-03
I would agree that things are becoming more polished, but I wouldn't equate that to oversimplification. A lot of the underlying complexities are still there, for what I've seen. 

If Ubuntu is leaning toward the everyday user, then some 'oversimplifications' -- like the splash screens and GUI refinements -- are unavoidable. I think that's great. And to be honest, when those features become unattractive, there are hundreds of less polished distros that are available.

---

### Post by aysiu on 2006-11-03
Sounds as if someone should be using KDE...

---

### Post by adam.tropics on 2006-11-03
> **aysiu said:**
> Sounds as if someone should be using KDE...

..or maybe even Gentoo !!

---

### Post by aysiu on 2006-11-03
> **adam.tropics said:**
> ..or maybe even Gentoo !!
Yes, that could work, too!

---

### Post by grte on 2006-11-03
Do you have a terminal emulator?

Not much you won't be able to accomplish with it.  Added bonus, it's definately not over-simplified.

---

### Post by jchau on 2006-11-03
> **bruenig said:**
> If you want your informative boot again, just edit the menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
and delete the quiet and splash options from it.

Thanks.

---

### Post by hyper7 on 2006-11-03
If the next build asks me my ASL, I'll agree with you.

---

### Post by Reshin on 2006-11-03
> **hyper7 said:**
> If the next build asks me my ASL, I'll agree with you.

A/S/L? O_o

---

### Post by blueturtl on 2006-11-03
I too am very disappointed with the screensaver issue, however it is a Gnome development rather than Ubuntu. A certain thread involving our great father-in-faith Mr. Torvalds comes to mind concerning a certain Gnome print dialog.

To summarize Mr. Torvalds: > having functionality polished or hidden is one thing, but removing functionality alltogether is not making things easier!

Even though I think KDE is the other extreme I do find it kind of disturbing that the Gnome people did not come to think many of us like to think of modifying our screensavers as *basic functionality* rather than advanced. Unless the Ubuntu devs go around by making their own app for things like these, we're stuck with the Gnome way. Complaining here won't help, we need to get this message to the Gnome devs. What was that Java based screensaver thingy btw? I'd sure be interested.

On the topic of is Ubuntu being oversimplified I'd still say no. This is because most of the things that are made simple are not done so by removing advanced functions (unlike the screensaver dialog). Case in point, the Ubuntu boot screen: it can be modified and so those who feel the need to see boot up messages can still do that. Many Ubuntu users might not need the commandline at all, but it is still there for all of us who enjoy and need it. Ubuntu IMO is in a very good balance for the time being.

---

### Post by TLE on 2006-11-05
As for the boot splash thingy I don't really care. I don't really understand the point about non-technical users, though i have seen it before I would think that even a non-technical user would understand the value of having diagnosis information if a problem accours, or to stay in this metaphor:
> **TheMono said:**
> Please, don't show the boot messages by default. Have the option, sure, but by way of metaphor, if I send someone to go pick me up a loaf of bread, I don't want a call every ten seconds saying "I'm starting the car now" "I'm taking a left" "Paying for the bread". I just want to be able to find out if something goes wrong.
If that guy never does return to you with your bread because a problem arose, then him shouting would definitely make it easier for you to find him and solve the problem wouldn't it? That should be understandable even to nontechnical users, who is the same users that if their WinXP fails to boot(which reports absolutely no info either) either reinstalls or panics and call a friend, who then come and reinstall because they can't figure out what the problem is without information

But as I said I don't really care much either way about that.

BUT what has been bothering me is, what I would definitely call an oversimplification, nomatter if it does come from Ubuntu or upstream from GNOME. I thought i was funny to modify the screen savers with fortune and what not but actually that's not to important to me. But one feature that I really liked was the ability to make it choose ramdomly form a subset of screensavers, which I thought was nice. Why did that feature need to go. Furthermore I don't think that is an "expert" option. As a matter of fact that is one of the things my girlfriend has commented positively on (She is still in windows and is not a computer-expert). I know it's a little silly but she really only needs an office package, music and msn and then when the work is done she likes to have fun with things like that, that look nice and do funny things and that would definitely be something she would apprciate once I DO install Ubuntu on her laptop.

Another thing is that when you acces the multiple desktop setting by right clicking on the desktop pager thingy at the bottom of the screen, the option that would allow the user to switch from the last desktop to the first and vice versa have also been removed.

I'm sure that either of these issues can be fixed by some sort of manual interventione but WHY did they have to go in the first place. Is it to advanced to let a user choose his favorite screensavers and &#314;et it choose ramdomly from those or let him change desktops from last to first. I think not. Both of those are definitely, absolutely clear cases of oversimplification if you ask me.

[QUOTE=aysiu]Sounds as if someone should be using KDE...[/QUOTE]
I think that's a little harsh. I agree with the qoute blueturtl posted
[QUOTE=Mr. Thorvalds]having functionality polished or hidden is one thing, but removing functionality alltogether is not making things easier![/QUOTE]
But maybe that's just me, or well the two of us, or no actually my pawl which is also a Ubuntu user has complainted about this to, so well the 3 of us anyway.

---

### Post by aysiu on 2006-11-05
> **TLE said:**
> As for the boot splash thingy I don't really care. I don't really understand the point about non-technical users, though i have seen it before I would think that even a non-technical user would understand the value of having diagnosis information if a problem accours Anecdotal evidence probably doesn't mean much, but for the record, the two people I've shown distros with a verbose bootup (Ubuntu Breezy and Knoppix 4.0.2) *loved* the scrolling text and found it refreshing and new. These were *not* technical users by any means, not "Windows power users" at all.

> **blueturtl said:**
> I too am very disappointed with the screensaver issue, however it is a Gnome development rather than Ubuntu. I disagree. Even though Ubuntu is tied closely to Gnome development, they don't have to go with Gnome defaults, as is shown in their choice of Firefox as the default browser (instead of Epiphany). They did not need to switch back to the Gnome screensaver (as opposed to X-Screensaver, which they used in the past).

---

### Post by pitkali on 2006-11-05
> **bruenig said:**
> If you want your informative boot again, just edit the menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
and delete the quiet and splash options from it.

You don't have to remove splash. If you remove just the both instances of quiet, you'll have splash with blue messages about things being done.

As for GNOME: I like it for it broad programming support - there's no mono binding for KDE. I haven't seen haskell binding neither. And the functionality that I have, suits me, most of the time. When it doesn't, I fire up gconf-editor ;)

---

### Post by TLE on 2006-11-05
> **aysiu said:**
> Anecdotal evidence probably doesn't mean much, but for the record, the two people I've shown distros with a verbose bootup (Ubuntu Breezy and Knoppix 4.0.2) *loved* the scrolling text and found it refreshing and new. These were *not* technical users by any means, not "Windows power users" at all.

Yeah well that's a good point. I **love** the scrolling text, I actually do in general like to see my computer do stuff :biggrin:
But I suppose that don't count since I **am** both a geek (study physics, like science fiction and love doing stuff with my computer) and a (at least) intermediate computer-user.

---

### Post by christhemonkey on 2006-11-05
My brother (who is completely non-computer-ish) loves the scrolling text on his dapper splash boot up!

He enjoys telling his friends about how his computer "boots the kernel" and "Mounts filesystems"

---

### Post by Kernel Sanders on 2006-11-05
Ubuntu is being designed with its own "Linux for human beings" mantra in mind.

As such, the ultimate aim is to have everyone feel comfortable doing anything in Ubuntu, regardless of computer proficiency, and for Ubuntu to be able to provide a way of actually doing the tasks that they are looking to do, again, regardless of computer proficiency.

Therefore, quite simply, its better this way! :p 

If it wasnt, Gentoo would be king, and be the choice of noobs as well as experienced users......and it most certainly isnt! :p

---

### Post by TLE on 2006-11-05
> ***John* said:**
> Ubuntu is being designed with its own "Linux for human beings" mantra in mind.

As such, the ultimate aim is to have everyone feel comfortable doing anything in Ubuntu, regardless of computer proficiency, and for Ubuntu to be able to provide a way of actually doing the tasks that they are looking to do, again, regardless of computer proficiency.

Therefore, quite simply, its better this way! :p 

If it wasnt, Gentoo would be king, and be the choice of noobs as well as experienced users......and it most certainly isnt! :p

Do you think the two examples I mentioned, of things that have been removed, is something which is nescessary to remove in order to make computer-newbies fell comfortable ?

---

### Post by aysiu on 2006-11-05
I can't think of a single user who would feel more comfortable **not** being able to choose the screensaver slideshow folder from the GUI.

If the user doesn't care about the screensaver, she won't even look at the screensaver options.

If she does care, she'll want to customize it. Why would you assume **everyone** wants to use what's in /usr/share/backgrounds? Most people I know who do slideshows want slideshows of their friends and family... or their pets.

---

### Post by Polygon on 2006-11-05
if you think gnome is getting too simplified, you can always just edit configuration files manually using gnome-terminal.

---

### Post by aysiu on 2006-11-05
> **Polygon said:**
> if you think gnome is getting too simplified, you can always just edit configuration files manually using gnome-terminal.
Yes, that is definitely targeting new users.

Why take away functionality that's useful to people?

It's not Gnome in general. Gnome in general is great. It's stupid things like the screensaver dialogue that doesn't give you basic options like choosing what folder to do the GL_Slideshow out of.

---

### Post by grte on 2006-11-05
> **aysiu said:**
> Yes, that is definitely targeting new users.

Why take away functionality that's useful to people?

It's not Gnome in general. Gnome in general is great. It's stupid things like the screensaver dialogue that doesn't give you basic options like choosing what folder to do the GL_Slideshow out of.

Yeah, but what's the point of getting up in arms about an app that, by it's very nature, you shouldn't be seeing that often?

Seriously, who cares what your monitor displays when you aren't looking at it?  I don't get it.

---

### Post by aysiu on 2006-11-05
> **grte said:**
> Yeah, but what's the point of getting up in arms about an app that, by it's very nature, you shouldn't be seeing that often?

Seriously, who cares what your monitor displays when you aren't looking at it?  I don't get it.
So, according to you, we should just get rid of screensavers altogether?

In fact, why even have a desktop background?

I think you're going to find yourself in the minority there...

---

### Post by chickengirl on 2006-11-05
> **grte said:**
> Seriously, who cares what your monitor displays when you aren't looking at it?  I don't get it.

This is exactly why I've stopped using screensavers at all. If it only comes on when I'm away, what's the point of having it do anything other than blank the screen? Therefore, that's what mine now does.

---

### Post by 23meg on 2006-11-05
[QUOTE=aysiu]They did not need to switch back to the Gnome screensaver (as opposed to X-Screensaver, which they used in the past).[/QUOTE]They [had a reason]("http://www.ubuntuforums.org/showpost.php?p=1314185&postcount=17"). As I understand it was a compromise, and a good one, unfortunately.

---

### Post by Gargamella on 2006-11-05
nonononono, you don't have to say so.
If you say this Linux will seem a computer-addicted toy forever.

It's important to semplify, you should understand this...this distro wants more and more users, anyway if you don't like it there are tons of other distros...this trend is gonna continue,surely

---

### Post by TLE on 2006-11-05
Once again, just so we are sure that we get this right!

[SIZE="3"][COLOR="Red"]Making simplifications DOES NOT EQUAL removing functionality
Making simplifications != removing functionality
Making simplifications \neq removing functionality[/COLOR][/SIZE]

---

### Post by Miguel on 2006-11-05
Because Xscreensaver is one of the killer apps of Linux/BSD. It has cool math representations, such as complex polhedra, 3D projection of hypersurfaces, nonperiodic penrose tiles (similar to a modern topic in crystallography) and spherical harmonics. It also has cool molecules, both lumpy or thin, and the chosen ones are the best: viagra, tetrahidrocannabinol, trinitrotoluene, some DNA components and, finally, ethanol. 

If not, you can always resort to firework display, fortunes sentence and, as a last resort, a picture slideshow of your girlfriend hitting you with a wipe for explaining her what those mathematical screensavers meant. 

Xscreensaver is the app that won't get ported to windows, it is the app that gets lots of oooohs and aaaahs from the people that use other OS'es, and can pull off an unexpected screensaver and have you drooling a bit, even when some results are waiting for you.

---

### Post by 23meg on 2006-11-05
[QUOTE=TLE]But one feature that I really liked was the ability to make it choose ramdomly form a subset of screensavers, which I thought was nice. Why did that feature need to go[/QUOTE]Because xscreensaver was replaced by gnome-screensaver altogether. All features "went", but they can come back. gnome-screensaver is yet at its infancy.
[QUOTE=TLE]Another thing is that when you acces the multiple desktop setting by right clicking on the desktop pager thingy at the bottom of the screen, the option that would allow the user to switch from the last desktop to the first and vice versa have also been removed.[/QUOTE]You mean "warping" from the last workspace to the first when using the scroll wheel to switch workspaces? If I'm not horribly wrong that feature wasn't there in the first place. You might be confusing it with XFCE's workspace switcher, which does have that feature, or another one.

---

### Post by grte on 2006-11-05
> **aysiu said:**
> So, according to you, we should just get rid of screensavers altogether?

While I don't use one myself, what I'm *actually* suggesting is that it's strange to me, the big deal that has been made over gnome-screensaver.  I mean...Really, how often do you watch your screensaver?  There's substance to the argument that functionality is being reduced, but surely there's a better poster boy than this.

[quote=aysiu]In fact, why even have a desktop background?[/quote]

Err...Because I see that.  It's used when I'm at the computer.

[quote=aysiu]I think you're going to find yourself in the minority there...[/QUOTE]

I can't be the only one who found it funny that the very next post was someone agreeing with me.

---

### Post by TLE on 2006-11-05
> **23meg said:**
> Because xscreensaver was replaced by gnome-screensaver altogether. All features "went", but they can come back. gnome-screensaver is yet at its infancy.
Yeah I read the post that was lnked to earlier about the rationale for the shift and it does seem reasonable. I hope we can get that feature back. Maybe I should be writing a dev or something
> **23meg said:**
> You mean "warping" from the last workspace to the first when using the scroll wheel to switch workspaces? If I'm not horribly wrong that feature wasn't there in the first place. You might be confusing it with XFCE's workspace switcher, which does have that feature, or another one.
I am faily certain though not 100% that it has been possible in Breezy

---

### Post by TLE on 2006-11-05
> **grte said:**
> ...There's substance to the argument that functionality is being reduced, but surely there's a better poster boy than this.

All right, as it turns out the sreensaver thing does seem to have a reasonable argument for the change. But in general I think the main reason this has made people rally is that: if it was truly that case, that it was policy to just cut without hesitation to "simplify", then we'd better have this discussion now before it happens to something more important something more people will miss.

---

### Post by esaym on 2006-11-05
Ubuntu is way too simple and I sadly can't get away from it :D

---

### Post by chaosgeisterchen on 2006-11-05
I can second the opinion that GNOME is getting more and more radically simplified. Simple and powerful is a great principle but if you really aim to take things away that users liked in former time it is most likely not a step which users will be fond of.

KDE is an overkill of options and I love it. GNOME should not be the other extreme but should reasonably limit the options to, on the one hand, make contolling it simple and, on the other hand, keep GUI dialogs for things which go a bit more into detail.

---

### Post by AskHL on 2006-11-05
Remember, people, we are not *just* talking about screensavers here. The screensaver subject is just an example.

Of course I cannot resist the temptation to continue the discussion about screensavers...

Some people point out that since the screensaver is not that important it shouldn't need that many options. I disagree: anyone who wants to configure this for one reason or other would want these options, so if we *do* take the trouble to provide screen savers, we might as well go the final yard and provide the appropriate controls. Whether they are in an "advanced"-menu or not can be discussed ("advanced"-menus surely cannot hurt casual computer users), but for the love of all that is good and holy, since we have taken the trouble to implement this in the first place -- and it works, people are using it -- don't just throw it away!

About the other example, i.e. the boot output, it is good that this can be reenabled by editing a particular file. But how would *I*, the intermediate user, or indeed *any* user know this (disclaimer: I haven't bothered to read all the help files so if this informations is actually there then sorry)? I just obtained the answer from this forum, so all is good and well... or is it? Why is it necessary to consult a *forum* to obtain information on how to do this? Shouldn't this be, like, the first thing in the "advanced" menu somewhere?

In a more general context I suppose you can stow all the hideous options away, that's fine. But please, *please*, don't *remove* the things some people want just because other people might not bother about them.

---

### Post by 23meg on 2006-11-06
> **AskHL said:**
>  Whether they are in an "advanced"-menu or not can be discussed ("advanced"-menus surely cannot hurt casual computer users), but for the love of all that is good and holy, since we have taken the trouble to implement this in the first place -- and it works, people are using it -- don't just throw it away!Please read the post I linked to in my first post; this move didn't take place because screensaver configuration was regarded as an unneeded "advanced" feature.

[QUOTE=AskHL]About the other example, i.e. the boot output, it is good that this can be reenabled by editing a particular file. But how would *I*, the intermediate user, or indeed *any* user know this (disclaimer: I haven't bothered to read all the help files so if this informations is actually there then sorry)? I just obtained the answer from this forum, so all is good and well... or is it? Why is it necessary to consult a *forum* to obtain information on how to do this? Shouldn't this be, like, the first thing in the "advanced" menu somewhere?[/QUOTE]I agree, it should be adjustable via a GUI dialog. But perhaps it's forgivable that it isn't, considering Edgy's shorter and busier than usual release process. 

Has anyone added a Feisty spec for "GUI toggling of boot text" yet?

---

### Post by ajm2005 on 2006-11-25
:)

---

### Post by ajm2005 on 2006-11-25
:)

---

### Post by coder_ on 2006-11-25
> This trend in Gnome towards hiding so much of the functionality is one of the reasons I'm considering going back to KDE.

I'm kind of with you here too. :S  But I prefer coding in Gtk than Qt :|
And KDE renders Baghira messed up on my system.  Also, I prefer the Gnome look if I can't have Baghira.

---

### Post by TeraDyne on 2006-11-25
After going from Ubuntu Breezy to Dapper and finally Edgy, I took a look at how many options I liked were hard to find or missing from the GUI, and just installed Kubuntu over it. I may like all the customizations, but when I can't find a simple "Color Scheme" customization when trying to select my theme, something is very wrong with the picture. Yeah, there's the configuration files, but it shouldn't be very hard to make a small dialog in the theme menu that asks what colors I'd like to use.

KDE is extremely customizable via the GUI without throwing an absurd amount of options at you. GNOME... not so much. It seems like GNOME is going towards the "Our users are dumb so let's dumb things down" route, while KDE seems to be shooting for the "Our users like to makes things work like THEY want it, so let's help them make those things work" sector. KDE, in all honesty, seems to be focusing on the USER, and more importantly the NEW USER. GNOME... well... I'm not exactly sure what kind of user they're focusing on. It's not for someone I know, and it's definitely not for someone like me who likes options.

There's a border between simple and "stupid simple", and GNOME, IMHO, has shot for and obtained the latter.

---

