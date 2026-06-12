---
title: "Defining a formal/transparent/public/safer process for nvidia-drivers in Ubuntu"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-17
*This is my suggestion for improving the way we deal with Nvidia drivers in Ubuntu, the way we handle Nvidia releases vs. Ubuntu Releases and how we can create a small process to Protect Ubuntu from breakage in exceptional cases. I might be completely wrong and have committed mistakes, and I *expect* people to point these and improve this specification. I will try to transmit this to QA, so they can discuss it with devs/release team.*

[SIZE=4]**RATIONALE**[/SIZE]
As far as I can understand, and looking at the info at [http://www.nvidia.com.br/object/unix.html](http://www.nvidia.com.br/object/unix.html), nvidia drivers are currently categorized in three branches. We can have a similar structure in Ubuntu and, additionaly, create a process to protect our users from breakage using a simple, publicly available, transparent formal process. The proces defines the packages, the naming convention and creates a 5 day interval in which we can test the packages in the case of updates. It also specifies which Ubuntu Releases will have which packages available in their repos.

[SIZE=3]**NVIDIA BRANCHES**[/SIZE]
[SIZE=2]**Long-lived Branch ("Stable")**[/SIZE]
Was 295.* until recently, right now it's 302.*, with 302.17 being the latest.
[http://www.phoronix.com/scan.php?page=news_item&px=OTkxOA](http://www.phoronix.com/scan.php?page=news_item&px=OTkxOA)

[SIZE=2]**Short-lived Branch ("Current" or "Beta")**[/SIZE]
304.*, with 304.43 being the latest

[SIZE=2]**Legacy Branch**[/SIZE]
71.*, 96.* and 173.*, depending on card - Not updated or updated periodically and only in extreme cases (i.e. vulnerabilities)
[http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM](http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTM)
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

I suggest we adopt a new naming convention and the associated testing process described below:

**[SIZE=4][B]NEW / SUGGESTED NAMING CONVENTION FOR NVIDIA DRIVERS PACKAGES**[/SIZE][/B]

**[SIZE=3]PACKAGES FOR LEGACY CARDS/GPUs (3):[/SIZE]**

**[SIZE=2]1) Package(s): nvidia-legacy-71, nvidia-legacy-96, nvidia-legacy-173[/SIZE]**
- The latest releases of the 3 legacy branches;
- Unsupported GPUs, will be updated rarely if ever. But some users need it;
- Available on Ubuntu Stable Release Repos (currently PP);
- Available on Ubuntu LTS and SRU Repos (also PP right now);
- Available on Ubuntu Development Release Repos (testers might need it in their machines);
- Obviously *not* available on "Proposed" repo.

**[SIZE=3]PACKAGES FOR UBUNTU STABLE AND LTS RELEASES:[/SIZE]**
**[SIZE=2]1) Package(s): nvidia-stable-proposed[/SIZE]**
- Only exists for a 5-working-days testing period;
- Is created when there's a Nvidia update to this branch;
- Is only available in "proposed" repos.
- The very latest release of the stable branch (long-lived). Currently 302.17.
- Will be updated regularly but, according to Nvidia, not with cutting-edge, install-borking changes;
- Even so, we should test it for at least 5 working days before it hits any repo;

**[SIZE=2]Testing Process (triggered by a new release/update to this branch):[/SIZE]**
- It is added to Ubuntu stable and lts releases *proposed* repo;
- QATeam is alerted via mail by developers/packagers of this push of nvidia-stable-proposed to SR/LTS proposed repo;
- QATeam starts a 5-working-days test of nvidia-stable-proposed. QATeam members receive the testing task via mail and use normal procedure (QA Tracker);
- A 5-working-days delay also allows us to have a little buffer in case a vulnerability or other serious regression is discovered within the Ubuntu community, Nvidia or the larger Linux community;
- After the 5-working-days testing period, testing results are available at QATeam tracker. If all is OK, nvidia-stable-proposed is moved from SR/LTS proposed repo to SR/LTS repos and renamed nvidia-stable.
- It is deleted from the "proposed repo".

**[SIZE=2]2) Package(s): nvidia-stable[/SIZE]**
- The latest release of the stable branch (long-lived) that passed a 5-day testing period, as described above;
- Available on Ubuntu Stable Release Repos (currently PP);
- Available on Ubuntu LTS and SRU Repos (also PP right now);
- *Not* available on "Proposed" repo (as explained above, it already migrated from it).

**[SIZE=3]PACKAGES FOR UBUNTU DEVELOPMENT RELEASES:[/SIZE]**
**[SIZE=2]1) Package(s): nvidia-current-proposed (or nvidia-beta-proposed)[/SIZE]**
- Only exists for a 5-working-days testing period;
- Is created when there's a Nvidia update to this branch;
- Is only available in "proposed" repos.
- The very latest release of the beta branch (short-lived). Currently 304.43;
- Will be more or less continously updated, according to our experience;
- Can bork a system or introduce serious regressions;
- We *must* test it for at least 5 working days before it hits any repo;

**[SIZE=2]Testing Process (triggered by a new release/update to this branch):[/SIZE]**
- It is added to Ubuntu development releases *proposed* repo;
- QATeam is alerted via mail by developers/packagers of this push of nvidia-current-proposed to DR proposed repo;
- QATeam starts a 5-working-days test of nvidia-current-proposed. QATeam members receive the testing task via mail and use normal procedure (QA Tracker);
- A 5-working-days delay also allows us to have a little buffer in case a vulnerability or other serious regression is discovered within the Ubuntu community, Nvidia or the larger Linux community;
- After the 5-working-days testing period, testing results are available at QATeam tracker. If all is OK, nvidia-current-proposed is moved from DR proposed repo to DR repos and renamed nvidia-current.
- It is deleted from the "proposed repo".

**[SIZE=2]2) Package(s): nvidia-current[/SIZE]**
- The latest release of the beta branch (short-lived) that passed a 5-day testing period, as described above;
- Available on Ubuntu Development Release Repos (currently QQ);
- Not available on Ubuntu LTS Repos (also PP right now);
- Maybe available on SRU repos (if it is considered a valid/safe update to Ubuntu Stable Release); 
- Available on Ubuntu Development Release Repos;
- *Not* available on "Proposed" repo (as explained above, it already migrated from it).

**[SIZE=4]Expected results:[/SIZE]**
- A clear naming convention that conforms to what nvidia adopts. 
- A publicly available and transparent policy to protect Ubuntu SR, LTS and DR. 
- A defined formal process that requires no investment or additional technology/personnel. It makes more sense to me. 

**[SIZE=4]RISKS AND OTHER CONSIDERATIONS:[/SIZE]**
- Ordinary users, which do not use "proposed" in their sources, will only see three packages: nvidia-legacy*, nvidia-stable and nvidia-current. I don't see a risk to them. In fact, I think we are reducing the risk to ordinary users when we create a formal process;
- nvidia-stable-proposed and nvidia-current-proposed will only exist for 5-working-days periods on the "proposed" repos, while we test them. They won't be seen by ordinary users.
- Risk is also reduced when a time-frame (5-days, as defined above) before a version migrates from proposed to the ordinary users repos is adopted. Our experience tells us how that could have helped in some situations;
- I can't see ways in which the adoption of such a formal procedure/process could imply in financial cost. But I do not work for Canonical and really don't know how these things are managed internally.

**EDIT:** Here a more visual summary of what I'm talking about:

[IMG]http://2.bp.blogspot.com/-lkuVJAufCbQ/UFgPd9L_kYI/AAAAAAAAACc/PfIERjcM4_U/s1600/nvidia-process.png[/IMG]

[SIZE=2](Download this table here: [ATTACH]224304[/ATTACH])
[/SIZE]
What do you guys think?

Regards,
Effenberg

---

### Post by Harry33 on 2012-09-18
Now Canonical has already made some changes.

The new beta Nvidia driver (nvidia-current_304.48) has been renamed to
nvidia-experimental_304.48.
This one conflicts with nvidia-current. Automatic installation (or with synaptic) will then remove nvidia-current when installing, but this does not happen when installing manually with dpkg => trouble ahead.

Also the package nvidia-settings_304.48 has been renamed to
nvidia-settings-experimental_304.48.
This one does not even conflict with nvidia-settings causing trouble.

This is a very bad practise and makes it more difficult to install a different driver version or flavour manually (from console or terminal).
Using "dpkg -i" will cause trouble or even breakage if the driver with a different naming is not purged first.

So the way I see it, all versions must have the same package naming.
The stable version only should always be in universe repo and the beta version should be found from proposed repo.

---

### Post by cariboo on 2012-09-18
Too add to the confusion, what about nvidia-current-updates? I really can't see any difference in the change-log, but my system won't run properly using nvidia-current, but does run quite well using nvidia-current-updates.

---

### Post by effenberg0x0 on 2012-09-18
I have added a table with a summary of what I'm talking about in the original post, just to (try to) be more clear. 

I think we should try to agree on one process, define it as best as we can, clearly explain why what we are proposing is better than no formal process or whatever is being used now and propose it together. 

In the end, it's up to us to try to make some change and improve things. I believe we can come up with a reasonable proposal and make it happen.
**EDIT:** And if we fail, at least we tried :) 

Regards,
Effenberg

---

### Post by balloons on 2012-09-18
I've not yet had a chance to read through your idea completely Alvaro, so I will withhold comment until I do :-) However, I didn't want to sit on this information as it is most relevant. There have been some changes to the nvidia and flgrx drivers:

Read these posts for background:
[https://lists.ubuntu.com/archives/technical-board/2012-August/001367.html](https://lists.ubuntu.com/archives/technical-board/2012-August/001367.html)
[https://lists.ubuntu.com/archives/technical-board/2012-August/001368.html](https://lists.ubuntu.com/archives/technical-board/2012-August/001368.html)

The technical board decided to offer a different -experimental package for each Nvidia beta driver series, in order that users can opt into them independently. They will have experimental in the package name.

The will all come with a warning about stability upon installation, and the typical SRU requirements will be waived. There will not be a one-week wait, and while people will respond to bugs about regressions, regressions and bugs can easily occur given the closed binary nature of the packages.

---

### Post by effenberg0x0 on 2012-09-18
> **guitara said:**
> I've not yet had a chance to read through your idea completely Alvaro, so I will withhold comment until I do :-) However, I didn't want to sit on this information as it is most relevant. There have been some changes to the nvidia and flgrx drivers:

Read these posts for background:
[https://lists.ubuntu.com/archives/technical-board/2012-August/001367.html](https://lists.ubuntu.com/archives/technical-board/2012-August/001367.html)
[https://lists.ubuntu.com/archives/technical-board/2012-August/001368.html](https://lists.ubuntu.com/archives/technical-board/2012-August/001368.html)

The technical board decided to offer a different -experimental package for each Nvidia beta driver series, in order that users can opt into them independently. They will have experimental in the package name.

The will all come with a warning about stability upon installation, and the typical SRU requirements will be waived. There will not be a one-week wait, and while people will respond to bugs about regressions, regressions and bugs can easily occur given the closed binary nature of the packages.

Thanks Nick, I'm waiting for your feedback.

I just wanted to point out that adding "-experimental" to nvidia packages is not enough. We should adapt to Nvidia's three-branched strategy and, at the same time, improve what we do in terms of quality and testing by testing updates to each of these branches in a safe environment.

IMO a better defined and public process that encompass "naming convention vs. repo vs. testing strategy" can make a huge difference in what we will provide our users with. I think we need something we can put on wiki.ubuntu.com so everyone can finally understand how we Ubuntu handles (or will always handle) Nvidia. 

If we can improve what I drafted above with inputs from the testers here (that have broad experience with Nvidia), your feedback and inputs from Devs/RT we can come up with something solid.

Regards,
Effenberg

---

### Post by xebian on 2012-09-18
My 2 cents.

Just KISS

nvidia-xxx.yy 

No confusion, and precise.

---

### Post by semperfried76 on 2012-09-18
Yes, this issue should definitely be straightened out. While I give the Ubuntu guys much props for including the 3.5 kernel (which straightened out my long-standing nvidia optimus woes), I must say that having to recompile the drivers every time the kernel was updated and having to go through the laborious process of figuring out if I needed nvidia-current, nvidia-current-updates, nvidia-whatever (and don't get me started on the time I tried to use the drivers from Nvidia themselves) nightmarish FAIL doesn't even begin to cover it...Some unified structure between Nvidia's own releases and Ubuntu's supported versions would be appreciated.

---

### Post by grahammechanical on 2012-09-18
Speaking as someone who has practically a non-existent knowledge of how things are processed in any Linux distribution, I say that the naming convention makes sense to me. But,

What good would these changes do if the testing part was not employed? 

There are community volunteer testers but it seems that at the moment the testing is done after any code changes are merged into whatever trunk or branch it is put in.

A lot of trust is placed in those who have upload rights. I do not think that they knowingly merge buggy code even in the development branch but I do think that they have become part of a process where bug reporting is the way to identify buggy code with corrections made later as the method of improving things.

I would like to see this changed to:

1) Testing by community volunteer testers prior to merging the code

2) then bug reporting along with some form of positive feed back that the code is not buggy, as the means to give Quality Control to merged code.

I would like to see this as a standard way of working for all major code changes in Ubuntu and not just Nvidia. Although I do accept that there has been and may still be (for all I know) a massive problem with Nvidia drivers. I no longer use them because of all the issues.

I was thinking of putting my ideas into a discussion document to see if between us we could come up with useful suggestions on how to add Quality Control to Quality Assurance.

Regards.

---

### Post by effenberg0x0 on 2012-09-18
> **grahammechanical said:**
> Speaking as someone who has practically a non-existent knowledge of how things are processed in any Linux distribution, I say that the naming convention makes sense to me. But,

What good would these changes do if the testing part was not employed? 

There are community volunteer testers but it seems that at the moment the testing is done after any code changes are merged into whatever trunk or branch it is put in.

A lot of trust is placed in those who have upload rights. I do not think that they knowingly merge buggy code even in the development branch but I do think that they have become part of a process where bug reporting is the way to identify buggy code with corrections made later as the method of improving things.

I would like to see this changed to:

1) Testing by community volunteer testers prior to merging the code

2) then bug reporting along with some form of positive feed back that the code is not buggy, as the means to give Quality Control to merged code.

I would like to see this as a standard way of working for all major code changes in Ubuntu and not just Nvidia. Although I do accept that there has been and may still be (for all I know) a massive problem with Nvidia drivers. I no longer use them because of all the issues.

I was thinking of putting my ideas into a discussion document to see if between us we could come up with useful suggestions on how to add Quality Control to Quality Assurance.

Regards.

I completely agree. The most important part of what I suggested above, in my opinion, is that new drivers released by Nvidia would enter Ubuntu via "proposed repos", to which testers will have access. And testers would have some time (I suggested 5 working days) to test and approve the new package or not. Then the new package would be moved from "proposed" repos to ordinary-users repos, and have it's name changed from "*-proposed" to it's proper branch name ("*-stable" or "*-current")only if it passed our testing. 

Approving or not approving a new driver release through a formal testing process is quality control. And it's what's lacking right now. We can fix that.

Regards,
Effenberg

---

### Post by semperfried76 on 2012-09-18
> **effenberg0x0 said:**
> 

Approving or not approving a new driver release through a formal testing process is quality control. And it's what's lacking right now. We can fix that.



Well said. I think a lack of quality control has been one of the main blockades to widespread Linux adoption.

---

### Post by effenberg0x0 on 2012-09-18
> **semperfried76 said:**
> Well said. I think a lack of quality control has been one of the main blockade to widespread Linux adoption.

I agree. I think the problem is that there are no "best practices" we can import, fund, adopt and enforce to our employees :) That's not how FOSS works. Whatever we, the community of contributors, decide to do becomes the best practice. 

Considering we can at least try to do something better (than what we have now), I don't see why not do it. In the  end, if we succeed and bring improvement to Ubuntu in this small Nvidia area, we can work to generalize and gradually expand whatever methods/process we define/adopt to other Ubuntu areas.

I think this is really important and has a long-term effect on Linux. FOSS and, obviously, Ubuntu adoption, branding and end-user perception. If anyone's interested in working in this ideas, writing suggestions for a formal process, improving and/or changing what I wrote above, preparing some material to present to Devs/Release Team, contributing with material you have already developed, etc I'd be more than happy to setup a Etherpad instance or Wiki page so we can work collaboratively.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-09-18
Hi Notorious Troublemaker :) :)

It would be nice if your suggestion was given a trial period and used as an experimental test-bed with the intention of expanding the idea into other areas of Ubuntu development.

I think that potential breakage points to consider as needing testing prior to merging changes are:

1) Grub
2) Xserver
3) video driver (proprietary and open source)
4) LightDM/Login Greeter
5) Desktop environment (Compiz/unity)

We know that there are many Ubuntu users that want to be part of a Ubuntu testing program that gives them a feeling of doing something useful other than reporting bugs. There are certainly enough testers to make small scale Community Volunteer Testing prior to merging a workable proposition.

Doing what you suggest with Nvidia drivers would be a nice place to start and it could be used to work out a method of testing and communication through the QA team that must surely help the developers get greater satisfaction from their work.

Regards.

---

### Post by effenberg0x0 on 2012-09-18
> **grahammechanical said:**
> Hi Notorious Troublemaker :) :)

Hey [Underwater explosives specialist]("https://wiki.ubuntu.com/LiveTesting") :)
> **grahammechanical said:**
> 
It would be nice if your suggestion was given a trial period and used as an experimental test-bed with the intention of expanding the idea into other areas of Ubuntu development.

I think that potential breakage points to consider as needing testing prior to merging changes are:

1) Grub
2) Xserver
3) video driver (proprietary and open source)
4) LightDM/Login Greeter
5) Desktop environment (Compiz/unity)

We know that there are many Ubuntu users that want to be part of a Ubuntu testing program that gives them a feeling of doing something useful other than reporting bugs. There are certainly enough testers to make small scale Community Volunteer Testing prior to merging a workable proposition.

Doing what you suggest with Nvidia drivers would be a nice place to start and it could be used to work out a method of testing and communication through the QA team that must surely help the developers get greater satisfaction from their work.

Regards.
You're absolutely right. Nvidia is a good starting point because it's urgent, it's wrong and we know how to fix it right now. We can start with it, see how far we can get, how the broader Ubuntu community and the technical teams accept our contribution and go from there to other areas. Remember we were 10 six months ago. Now we're 90 and growing. We are Ubuntu testing whether we accept to use that label or not. It's about time we drop our QQ stall and get to work :) It's a good thing we did all that writing back when the team started. A lot of that makes sense and can be used right now. 

I'd like to hear what Nick has to say about endorsing the results or our work (in this specific case the suggested specs/process for Nvidia Quality) and pushing it to Devs/RT. We always complained (still do) about the lack of info, gap between Devs/RT/TB and testers. It makes sense to work with QA as the bridge in this. If QATeam is not into this, than we would have to think off and use entirely different approaches.

Let's get this feedback and organize after that.

Regards,
Effenberg

---

