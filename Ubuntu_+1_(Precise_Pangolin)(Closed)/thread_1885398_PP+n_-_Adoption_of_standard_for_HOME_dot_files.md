---
title: "PP+n - Adoption of standard for HOME dot files"
date: 2011-11-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-23
I don't believe there has ever been any effort or development of set of guidelines to organize dot files created inside user $HOME. While some apps have converged to using the $HOME/.config/<App_Name>/<Config_File> structure, we still have a lot of config files elsewhere.

From the perspective of IT management, it would be wise (and professional) to have all dot files inside .config at every home folder IMO. 

Many programs have global settings (at /etc) that specify where to look for users config files, so it could be changed easily. A lot of other programs have it harcoded, but changing it requires almost no effort and knowledge of the code structure in the programming language used. 

Do you agree that it would be a good idea to:
- Request Ubuntu projects to use $HOME/.config/<app_name>/<app_files> structure
- Request packagers to ensure that the application they maintain is using this standard.
- Publish as Ubuntu guideline, etc.

I know gconf/dconf may eventually improve this, but we must consider some applications won't use it now, or ever. A system with 1 or 2 years of normal use is normally infested of dot files saved in very different ways inside $HOME. As Linux/Ubuntu evolves into a more professional and tidy environment, I think it can't be good to hold on to this habit much longer. Messing with this is the kind of bold step only a distro such as Ubuntu can take.

I'd like to hear some opinions, if you think this is a valid idea and, if so, how we could work together to take this request to the right people.

---

### Post by MacUntu on 2011-11-23
So you want thousands of Ubuntu patches to make those apps put their config files in one place? What about upgrade paths (you need to make sure to carry over "old" config files)? Sounds like mission impossible to me. :P

> **effenberg0x0 said:**
> Do you agree that it would be a good idea to:
- Request Ubuntu projects to use $HOME/.config/<app_name>/<app_files> structure
- Request packagers to ensure that the application they maintain is using this standard.
- Publish as Ubuntu guideline, etc.
@1. Most applications aren't Ubuntu projects.
@2. Packagers usually don't wildly patch applications to use different paths.
@3. How many application authors are willing to do something Ubuntu-specific?

I do agree, would be nice, but I don't see it happen. As long as those dot files have a proper name, it's bearable for me.

---

### Post by dino99 on 2011-11-23
the main issues i can see is to resolve settings conflicts by using different app releases coming from several distro (example: FF4/5/6/7/8  on lucid/maverick/natty/oneiric/precise) and sharing a unique /home partition.

I've filled such bug by the past, to request config file setting attached to each different distro, to avoid such possible conflicts, but have always been declared as invalid/wontfix sadly.

---

### Post by effenberg0x0 on 2011-11-23
> **MacUntu said:**
> So you want thousands of Ubuntu patches to make those apps put their config files in one place? What about upgrade paths (you need to make sure to carry over "old" config files)? Sounds like mission impossible to me. :P


@1. Most applications aren't Ubuntu projects.
@2. Packagers usually don't wildly patch applications to use different paths.
@3. How many application authors are willing to do something Ubuntu-specific?

I do agree, would be nice, but I don't see it happen. As long as those dot files have a proper name, it's bearable for me.

Thanks for your reply.

I'm not saying it would be easy, fast or entirely successful. But, I tend to believe that *having* some guidelines, is better than having none. 

**1**. But some are, and yet there's no standard.
**2**. Patches for new installs would be easy, honestly. Mostly every decently-written program concentrates file r/w function within one file. Patching this is a two lines patch. In the case of the (many) that use glib to r/w to disk, a standard patch can grep/fix lots of projects in one minute. Same for std C/C++. Python too, etc. Summarizing, it is not the end of the world. 
**3**: You'd be surprised how many developers consider Ubuntu to be one of (if not the most) relevant distro (as it has more users, market share, mind share, etc). The days in which was not respected by developers are long gone. Commercial apps, for example, are developed today ensuring compatibility to Ubuntu releases. I see that everyday.  

I think most ideas and changes aren't really easy. They are attempts that may or may not work in the long run. But someone's gotta try.

---

### Post by dino99 on 2011-11-23
you might open a brainstorm thread to get streamed idea on such request

---

### Post by effenberg0x0 on 2011-11-23
> **dino99 said:**
> the main issues i can see is to resolve settings conflicts by using different app releases coming from several distro (example: FF4/5/6/7/8  on lucid/maverick/natty/oneiric/precise) and sharing a unique /home partition.

I've filled such bug by the past, to request config file setting attached to each different distro, to avoid such possible conflicts, but have always been declared as invalid/wontfix sadly.

Hi Dino,
It makes sense to me, I hadn't thought of such case. I deal with a couple others here and have my hacks to make it work (many soft links, etc). It's a situations that could benefit from standards, for sure.

---

### Post by effenberg0x0 on 2011-11-23
> **dino99 said:**
> you might open a brainstorm thread to get streamed idea on such request

I probably would, but IMO it's not something I'd ever get  to transform into a Ubuntu project/priority or get any sort of  endorsement. 
 
I'm against enforcing anything. I'm thinking on the lines of writing some sort of "Open Proposal for Standards" which would:

- Define the proposed standard
- List the cases in which they are needed
- Exemplify with real situations, like the one you mentioned
- Provide examples on how to change code to use the proposed standard
- Provide scripts that packagers can use to safely / rapidly auto-fix  sources that use some common languages, like C, C++, Vala, Python, etc.

I'd publish the open proposal somewhere, mail as much developers and  packagers as I can to request their adherence, feedback and help  inviting other developers to adhere. Maybe as some projects adhere, others would  eventually follow the same lines, which would end up affecting not only  Ubuntu but other distros.

---

### Post by dino99 on 2011-11-23
> **effenberg0x0 said:**
> Hi Dino,
It makes sense to me, I hadn't thought of such case. I deal with a couple others here and have my hacks to make it work (many soft links, etc). It's a situations that could benefit from standards, for sure.

I've seen conflicts mainly when a distro have made a big move on gcc/udev/hal and/or split package in several smaller ones, and/or add/drop dependencies.
As a unique /home user, and dont want to have multiple ones, i think that having dedicated dot files for each distro make sense too (like .config, .gconf, ...) and should not be that hard to set and add to specific ubuntu already applied config (app-install-data).

---

### Post by dino99 on 2011-11-23
> **effenberg0x0 said:**
> I probably would, but IMO it's not something I'd ever get  to transform into a Ubuntu project/priority or get any sort of  endorsement. 
 
I'm against enforcing anything. I'm thinking on the lines of writing some sort of "Open Proposal for Standards" which would:

- Define the proposed standard
- List the cases in which they are needed
- Exemplify with real situations, like the one you mentioned
- Provide examples on how to change code to use the proposed standard
- Provide scripts that packagers can use to safely / rapidly auto-fix  sources that use some common languages, like C, C++, Vala, Python, etc.

I'd publish the open proposal somewhere, mail as much developers and  packagers as I can to request their adherence, feedback and help  inviting other developers to adhere. Maybe as some projects adhere, others would  eventually follow the same lines, which would end up affecting not only  Ubuntu but other distros.

You get my full support :)

---

### Post by stevemot on 2011-11-23
Actually, the "standard" already exists - it's the [freedesktop.org XDG Base Directory Specification]("http://standards.freedesktop.org/basedir-spec/latest/"). (Though freedesktop.org now seems to be back-pedalling from calling itself a standards organisation).

The issue is of course, as others have said above, making upstream projects aware that the standard exists, and persuading them to adopt it. At least though there is an official standard folks can point at when trying to persuade them...

---

### Post by SevenMachines on 2011-11-23
I seem to remember theres a freedesktop specification about this ($XDG_CONFIG_HOM[FONT=Verdana]E ? ). Don't know how well adopted it is though, but that would be the thing to use

[EDIT] As [/FONT][stevemot]("http://ubuntuforums.org/member.php?u=144443") says :)

---

### Post by ronacc on 2011-11-23
has anyone considered that this lack of rigid standardization contributes to the relative scarcity of viruses/malware directed at linux ? on a windows system or even a mac you know where the type of file you are intending to corrupt or install is located , this is not so in linux where even system files may vary in their location from distro to distro .

---

### Post by dino99 on 2011-11-23
> **ronacc said:**
> has anyone considered that this lack of rigid standardization contributes to the relative scarcity of viruses/malware directed at linux ? on a windows system or even a mac you know where the type of file you are intending to corrupt or install is located , this is not so in linux where even system files may vary in their location from distro to distro .

even if files can be located into some different folder/subfolder, finding them with a routine is not a problem. All that matter is the allocated rights on such files/folders. You surely know that linux sources are open & all the associated apps too, and its not an open gate for kiddy script.

---

### Post by effenberg0x0 on 2011-11-23
One could suppose that main binary files in a Linux system are either under /bin or /sbin. Other bins (/usr/bin, /usr/sbin, etc) may or may not be there, I wouldn't write something to attack it with no fallback/detect process. Nonetheless, any standard ps aux | grep -i <something_bin>, pidof, mlocate, whereis, find, which, cat /proc/something, etc could be used. The reason we don't have such problems on Linux relies almost entirely in the permissions/ownership structure plus firewall IMO. Sources are open, everybody knows everything.

But when we're talking about dot files, text, owned by $USER:$USER/775 or more restrictive, I think no one really cares much about security,  either spread all over $HOME or at $HOME/.whatever/*. And, God forbid we ever rely on disorganization and lack of good practices and standards to increase security :) 

@stevemot @sevenmachines I'll have a look at the XDG standard, thank you for the info!

---

### Post by ronacc on 2011-11-23
I didn't say that it was the only thing or even a major one , just that it may contribute , and I certainly wouldn't rely on it as my sole protection .

---

### Post by seeker5528 on 2011-11-25
> **stevemot said:**
> Actually, the "standard" already exists - it's the [freedesktop.org XDG Base Directory Specification]("http://standards.freedesktop.org/basedir-spec/latest/"). (Though freedesktop.org now seems to be back-pedalling from calling itself a standards organisation).

Back-pedalling would require them to have called themselves a standards organization to begin with.

Freedesktop.org was never considered a standards organization by the people who created and maintain it, and I expect not by most of the people that have used the services freedesktop.org provides either. It was/is a place where people could work on stuff and try to build consensus on standardizing some system components, configuration formats, file locations, etc...

LSB is the standards organization, and for a significant portion of stuff adopted by the LSB consensus was already built elsewhere, some of it at freedesktop.org.

Later, Seeker

---

### Post by seeker5528 on 2011-11-25
> **dino99 said:**
> the main issues i can see is to resolve settings conflicts by using different app releases coming from several distro (example: FF4/5/6/7/8  on lucid/maverick/natty/oneiric/precise) and sharing a unique /home partition.

I've filled such bug by the past, to request config file setting attached to each different distro, to avoid such possible conflicts, but have always been declared as invalid/wontfix sadly.

I can't imagine that any distribution vendors would support multiple versions of their own distro using the same '/home/' directory, much less other distros.

Doing so would require creating non-standard configuration directories/file names, which kind of defeats the purpose of standardization.

It would also mean the disto vendors would have to do a bunch of work on migration stuff to handle upgrades, which would most commonly be handled by the applications/suites of applications because the developers of these things typically build the migration in when config or other file formats change or default locations for these things change.

If you want applications in each distribution and each version of each distribution to have their own settings, then there is this little thing called "don't create a seperate '/home/' partition" that may be of use to you. ;) You could always have a seperate partition for music, documents, etc... that you create one or more symlinks to in your different '/home/' directories, keep your email on the server, sync bookmarks, etc..., it's saner and not much, if any, harder to manage permissions than attempting to share a common '/home/' partition.

Later, Seeker

---

