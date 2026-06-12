---
title: "Just Curious (regarding ubuntu development rolling)"
date: 2013-05-18
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-05-18
I didn't follow the latest discussions at the ubuntu developers meetings...anything new about adding that easier "rolling" way to use ubuntu development that they had previously discussed?
Have they decided on the method and when it would be implemented?

I wasn't sure whether it was discussed but i am curious about it...

Thanks :)

---

### Post by Elfy on 2013-05-18
I think it is somewhere in this 

[http://summit.ubuntu.com/uds-1305/meeting/21761/foundations-1305-development-release-planning/](http://summit.ubuntu.com/uds-1305/meeting/21761/foundations-1305-development-release-planning/)

---

### Post by deadite66 on 2013-05-18
From what i've read it seems they are releasing monthly point releases from the development branch and these "should" be stable.

---

### Post by grahammechanical on 2013-05-18
You know how we change from one development release to the next by changing the URL of the sources lists? Such as changing them from raring to saucy? Well the rolling development branch, as I call it, will be given a name, such as TIP, NEXT or ROLLING (this bit is still be be decided) and that name will be the name in our sources lists URL. At the repository end there will be a sym-link that points to the correct repository. Then when 13.04 is released the sym-link will be changed at the repository end to point to the repositories of TT (14.04 to be). We will not have to change anything.

Implementation? In my mind the logical time will be as soon as 13.04 is released. So, we change to TT (14.04) development cycle and it continues from there on to 14.10, 15.04.

Regards.

---

### Post by craig10x on 2013-05-18
@grahammechanical:  you meant when 13.10 is released it will change to TT or whatever other name they decide as you mentioned (starting with the 14.04 development cycle) right?
I figured that was just a typo ;)

So, in essence, i guess that would mean that when the first 14.04 daily builds appear (right after 13.10's release) it would have that new permanent name assigned to it, so that from that point on, you would no longer need to upgrade into the next development cycle....am i reading that right? :D

Also, i am listening to that video right now...it also sounds like we would get monthly stable updates within the rolling development...so i guess that means instead of getting constant daily updating it would be more like a monthly update package coming into it? (sort of the way linux mint's LMDE works)...or perhaps i misunderstood what they were saying...

---

### Post by Chanath on 2013-05-19
Simply by changing the repos to the latest testing, you are on rolling. When Saucy is finally released, you change the repo name in the sources.list to the next one.:)

---

### Post by cariboo on 2013-05-19
For those of you that don't have etherpad access, these are some of the points that were discussed:

> This is expected to be fairly easy technically.  The messaging is important.

Things we could do to encourage folks to track dev releases (outside of improving quality and providing a devel suite symlink):
* software-properties option to always stick to development release (make sure that switching back works!); only show this on people already on the devel release though
* website messaging?
* uploader support for uploading to current

Might have to fix various pieces to be able to install from this symlink

Would uploads be directed at the devel symlink?  Not sure whether this is contentious or not; probably minor

Some developers are concerned by the number of releases they have to target; one of the reasons is that the uploader is kept open as to support commercial projects/PPAs

market to app developers: developer.ubuntu.com

Implementation:

Arrange for there to be a symlink from something like 'devel' 'current' or similar to the current development release.  This would be made via a small patch to launchpad.  We would want to be able to install from this as well.


For developing on 'devel' releases, all the build artifacts would need to know about it: sbuild, schroot, chdist, etc.

Also what about d/changelogs?  Would they name the current release or 'devel'?  If the latter, it would be more difficult to know when the package was uploaded for. == was covered above ("uploads directed at the devel symlink"); need to decide whether we want that on e.g. ubuntu-devel@ or such

It is unclear when 'current' should move from raring to saucy in the cycle.  We nominally say that the release is not ready for use until we have uploaded the rcompilers etc at the beginning of the cycle, ie. till when it comes out of pre-release-freeze at the beginning.  We might want to hold the move until that kind of level of readiness before we move it over.

Some discussion on making sure the name helps to reinforce the SLA we are driving at.  xorg-edgers put up as a good example.  We must avoid any name from debian (which kills testing and unstable).

Would want to allow reverting back to the current devel release and stick to it; probably in software properties too

Candidate names:
 * development
 * current
 * tip
 * latest
 * head
 * master
 * devel
 * trunk
 * rolling
 * bikeshed :)
 * next
 * nonameyet

Excluded:
 * sid, testing, unstable or other Debian names
 * rawhide
 * factory

Work Items:
[rick-rickspencer3] pick a name for the release and bring to TB
[rick-rickspencer3] follow up with the community team on this
[cjwatson] chase someone to implement software-properties changes
[cjwatson] talk to Kubuntu guys about equivalent Qt version


---

### Post by craig10x on 2013-05-19
Very Informative.....i think what i am most confused about though is this....if i say, installed saucy development (13.10), will they be updating the name in your software sources to whatever that new name will be, and then you'd just smoothly switch over to 14.04, or would you have to do something yourself....

I would imagine that when 14.04 development starts, it would already have the new name, but i was wondering what would happen with those currently running 13.10...how it would for them...

I'm also confused about whether the updates for the rolling development continue to be daily or monthly as they did mention something about monthly stable snapshots as it were...

Lastly, it sounds like you'd always be able to choose between making it rolling or switching it back to non-rolling...i wondered about that also...

---

### Post by Elfy on 2013-05-19
Who can tell - until they actually tell us what they've decided then this thread will go round and round in circles like your last one on exactly the same subject ;)

---

### Post by craig10x on 2013-05-19
Yeah, I guess so, Elfy...I was just trying to decipher the information...hopefully we will get more clarity soon...sounds interesting though, and i just like to keep on top of it :D
I appreciate the link you gave to the conference video, by watching, at least i got SOME idea of what they are going to be doing...

---

### Post by grahammechanical on 2013-05-20
@craig10x

I think of those vUDs sessions as discussion sessions and not executive decision making sessions. At the first vUDS they discussed the proposal for making a Ubuntu rolling release available but they did not discuss the practical methods of bringing it about. So, they set up a session at this second vUDS to discuss specifically the practical methods that would be needed. Now there needs to be consultation and decision making. We may get a third session at the next vUDS in 3 months time that will be like a progress report.

I am guessing that the change over will happen at the point that Saucy development ends and T<name> development begins. And we will have make the change to our sources URL ourselves. Otherwise, anyone running Saucy development will be forced onto T<name> development. But once will have pointed our sources URL to the rolling symlink then we will not need to do anything else to go from T<name> development to U<name> development branch. So, the development branch becomes a rolling, daily updated release but not in the same way as other distros have a rolling release version.

I do not remember any discussion at this session about monthly snapshots. Those snapshots are a QA thing and were discussed some weeks ago, perhaps at the first vUDS. There are five months still to go for Saucy development. QA needs to coordinate its activities and vUDS sessions are useful for doing that especially since QA now has greater responsibility; testing Ubuntu Touch during this cycle and desktop convergence during the next cycle.

Anyone who installs a T<name> monthly snapshot will get T<name> development that through daily updates will become T<name> released (14.04). They will not get Ubuntu rolling development unless they change the sources URL to point to the Rolling symlink.

There was also a session in Unity 8 + MIR on 13.10 desktop preview. It will not be put in the final 13.10 ISO image. It will have to be brought in through a PPA for those who choose to do it knowing the risks of installin a preview. The focus for this cycle is Ubuntu Touch on mobile. The focus for next cycle will be the convergence of Ubuntu Touch (Unity 8 + MIR) on the desktop. This is not to say that the Unity 8 + MIR code will not be available to those of us on the Saucy development branch. This preview will be available either through the proposed repository or through a PPA so that it can be tested before it is moved into the Main repository. The emphasis is on Daily Quality which is proved through daily updates.

Regards.

---

### Post by craig10x on 2013-05-20
Very good...yes i think i get a much clearer picture now about how it should likely work...so let's say i was running 14.04 development...from what i gather, it would simply become 14.04 final when development is finished with it, unless i did the option of pointing the sources URL to the rolling release symlink...in order to move into the rolling method of development...

However, would that not likely be some different type of terminal command you would enter to point to the symlink?
You would not be using the current "upgrade your source list" method that you currently use here, right?

That would be better for me, since i messed up when trying to use the current method...so i am rather "gun shy" about attempting it again...

I'd assume you'd only have to use the current "upgrade your sources list" method on 13.10 since it does not have the new permanent name for development.

---

### Post by grahammechanical on 2013-05-20
We will see what is said closer the date. I am also nervous when running commands. This command would do it.

```
sudo sed -i 's/saucy/rolling/g' /etc/apt/sources.list
```

assuming the the chosen name is rolling. Perhaps when get confirmation someone on this section will write out a script containing the necessary commands to make it easier for those of us who frequently mistype.

Regards.

---

### Post by craig10x on 2013-05-20
thanks...ah, i see what you mean...whatever development version you would be running (ex: saucy is 13.10...14.04 something with a T in it of course....let's call it TT since i don't know what it will be called)...
you would simply use a command like you just mentioned and that would move it into rolling...so if you were running 13.10, that's how you would do it...If running 14.04, again, that 's how you would do it (with the TT name instead of saucy of course)...

that would be easy...i just don't like playing around with making manual adjustments on a source list....that is where i "messed up" when i was trying to upgrade from 13.04 development to 13.10 development...
if it was simply a matter of putting in a symlink command as you outlined, that sounds like it should go smoothly...

and i also sometimes mistype....which is why i like it when someone posts it correctly and then i just have to "copy and paste" :)

---

