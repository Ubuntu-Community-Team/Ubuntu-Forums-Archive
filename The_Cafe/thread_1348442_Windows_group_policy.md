---
title: "Windows group policy"
date: 2009-12-07
forum: The Cafe
---

### Post by aquavitae on 2009-12-07
I'm not sure where the right place is for this question - probably in a windows forum, but I think that any windows-knowledgeable ubuntuers will probably be far more helpful. 

At work, the companies group policy dictates that I cannot move or add toolbars in windows explorer (win XP).  This is really frustrating, and as far as I can see, completely pointless!  Does anyone know of a way around this restriction?

---

### Post by winjeel on 2009-12-07
I can only suggest to talk to the company tech guy and ask for an exception or Firefox for your work computer.

---

### Post by Tristam Green on 2009-12-07
It was probably insurance to prevent people from installing additional toolbars like Google/Yahoo/MSN/CometCursor etc.

If it's passed through GPO, the only way to get around it is to disjoin from your corporate domain, login as the local administrator, change the local policy settings manually, and don't rejoin.

Of course, then you lose authentication, access to network resources, etc etc.

In short, you're at the mercy of your IT Infrastructure while you're working, so be nice to them :)

---

### Post by rickyjones on 2009-12-07
> **winjeel said:**
> I can only suggest to talk to the company tech guy and ask for an exception or Firefox for your work computer.

Seconded.

The point of group policy is to manage the computers centrally so that the end users do not modify things that they shouldn't be modifying. Talking to the IT people might get you somewhere. Beyond that if you have access to the Registry then you could manually undo any policies, but they will be reapplied as soon as group policy refreshes itself, usually every 90 minutes.

Thanks,
Richard

---

### Post by aquavitae on 2009-12-08
Thanks for the info. I've learnt that talking to IT won't help for these sort of things - its difficult enough getting them to respond to the major problems.  I do have access to the registry but I'm not sure what to change.  Its just really annoying me that I can't add a links toolbar to windows explorer! I use firefox for web browsing anyway. The other option, I suppose is to use an alternative file browser.  Anyone know of a good one that runs well in windows?  Opensource preferably!

---

### Post by LinuxFanBoi on 2009-12-08
> **aquavitae said:**
>  Does anyone know of a way around this restriction?

That depends on if your group policy allows you to resize your hard drive's partitions or not.  If it does,  your solution is waiting for you [here]("http://www.ubuntu.com/getubuntu/download").

---

### Post by aquavitae on 2009-12-08
> **LinuxFanBoi said:**
> That depends on if your group policy allows you to resize your hard drives partitions or not.  If it does,  your solution is waiting for you [here]("http://www.ubuntu.com/getubuntu/download").
Thanks, I've already done that ;) The trouble is that quite of lot of software I use doesn't work in linux. E.g. autocad, arcgis. Also, we're on an exchange server and so far I've had no luck in getting evolution to work with it.

---

### Post by Icehuck on 2009-12-08
You are going to be stuck with whatever settings they dictate. You can make changes to the registry, but the machine will update the policy after about an hour. If they are really strict you can see policy updated in less then 30 minutes.

---

### Post by LinuxFanBoi on 2009-12-08
> **aquavitae said:**
> Thanks, I've already done that ;) The trouble is that quite of lot of software I use doesn't work in linux. E.g. autocad, arcgis. Also, we're on an exchange server and so far I've had no luck in getting evolution to work with it.

I only hope that you don't get caught or that you have authorization to do that to your work computers.  I know a guy who was fired for checking his fantasy football scores on a work computer.  To be honest though they where looking for any reason they could to get rid of staff hired under previous ownership,  but that's beside the point.

---

### Post by Icehuck on 2009-12-08
> **LinuxFanBoi said:**
> I only hope that you don't get caught or that you have authorization to do that to your work computers.  I know a guy who was fired for checking his fantasy football scores on a work computer.  To be honest though they where looking for any reason they could to get rid of staff hired under previous ownership,  but that's beside the point.

If your IT staff is like me, they will do their best to get you fired. Change my machines without permission, and it's war.

---

### Post by lisati on 2009-12-08
/me thinks back to when I was working. The process I sometimes used to fix problems on the company's mainframe went something like this:
[LIST=1]
[*]Colleague says something along the lines of "Dang it, something has gone wrong"
[*]Ring official help desk, in the interests of doing things through proper channels.
[*]End result of phone call: muttering to the effect "Dang it, that wasn't much help! Incompetent <censored>!" (person at help desk probably thinking something similar) ](*,)
[*]Scratches head, looks through department's reference books, and eventually finds an answer which would work if one had access to main system console.
[*]Scratches head again, and remembers overhearing something or reading about a trick to let you put the necessary command(s) in remotely. (hush, don't tell anyone!)
[*]Does necessary sneaky activities; problem fixed, to the amazement of some colleagues.
[*]Boss and colleagues eventually learn that the "fix" was applied somewhat sneakily instead of through proper channels. Lecture follows. ](*,)
[/LIST]
Edit: N.B. [http://ubuntuforums.org/showpost.php?p=8460678&postcount=14](http://ubuntuforums.org/showpost.php?p=8460678&postcount=14)

---

### Post by toupeiro on 2009-12-08
Group policies enforce themselves by backend services that are tied into active directory and they run on timed intervals.  So, even if you did find a way to unset a particular policy, it would reset itself.  I know of ways to do this but you risk your machine being able to participate fully on your AD domain, which opens the doors to even more problems potentially if they're doing GPO effectively.  More importantly, I think it defeats the ethics of this board's CoC and of your companies use policy more than likely so I will leave it at that.

Group policies like the ones you are talking about are there to protect business assets.  They obviously don't want you adding toolbars to your web browser so my advice would be, follow the rules, and if you really have a business need for a toolbar, get your IT people to do it for you because a GPO setup properly would definitely remove it even if you did get it in there.

---

### Post by ade234uk on 2009-12-08
Its all a load of ********. These system admins make their life difficult. Its Internet Explorer or nothing, the question is why?

Why don't they trust alternatives, when the product they are currently using is unsafe and poor quality.

Its like on the news warning the general public to be careful for viruses and to keep Internet Explorer updated, but they never say a safer option would be to use Firefox do they?

I just find the whole thing frustrating. After sitting at work using Windows XP every day, its a joy to use Ubuntu.

---

### Post by cariboo on 2009-12-08
toupeiro, is correct it is against forum policy to help you circumvent policies at work. Thread CLosed.

---

### Post by toupeiro on 2009-12-08
> **ade234uk said:**
> Its all a load of ********. These system admins make their life difficult. Its Internet Explorer or nothing, the question is why?

Why don't they trust alternatives, when the product they are currently using is unsafe and poor quality.

Its like on the news warning the general public to be careful for viruses and to keep Internet Explorer updated, but they never say a safer option would be to use Firefox do they?

I just find the whole thing frustrating. After sitting at work using Windows XP every day, its a joy to use Ubuntu.

It's their investment, and they can do whatever they want.  Start your own company and run 100% FOSS.  More power to you.  But if you're not a CTO, or in a position to make changes like this in your company, then don't.  If you really hate it enough, quit. :P

---

