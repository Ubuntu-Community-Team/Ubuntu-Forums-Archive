---
title: "no results in dash &quot;Applications&quot; or &quot;Home&quot; tabs"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by montini on 2012-03-27
After installing some recent updates, unity dash doesn't find any applications when typing something into search field. It only shows the results from "Videos" and "Music", but no Application results. Also, initialy, after opening the dash, there are no "recently used" icons in the dash "Home" tab, nor in the "Applications" tab. 

How could that be fixed? The only way to start the application now is through [Alt]+[F2].

---

### Post by montini on 2012-03-28
anyone?

---

### Post by stinkeye on 2012-03-28
If you can log in as another user and it works,
try removing unity related folders from **~/.cache**

---

### Post by montini on 2012-03-28
You were right, when logged in as guest, the problem disappears, but when I tried to "rm -rf unity*" (under normal user account) it didn't help - I still get only Video and Music results - and in the ".cache/" folder the "unity-lens-video" folder reappears. Maybe there is another place where I should purge the chache?

---

### Post by cariboo on 2012-03-28
Have you tried:

```
unity --reset
```

either in a terminal, or in a console.

---

### Post by montini on 2012-03-28
I did, with no luck.

---

### Post by Elfy on 2012-03-28
Same here.

Login as guest  - no results

Delete unity folders - no results

unity --reset - no results

---

### Post by montini on 2012-03-28
for me, logging in as guest means the problem's not there, i.e. it works correctly there.
I assume erasing all the hidden folders under "~/" would help, but wouldn't want to loose all the settings.

---

### Post by montini on 2012-03-28
found the solution: you should erase the zeitgeist databases. Of course, you lose the activity information, but at least it works from that point on.

so, the command should be (insert via terminal):
```

cd ~/.local/share/
sudo rm -rf zeitgeist

```

That's it.

---

### Post by Elfy on 2012-03-28
I'll remove it now via xubuntu and see what it's like next time I boot - thanks montini.

---

### Post by Elfy on 2012-03-29
No change - at some point I'll reinstall.

Thankfully I don't use Ubuntu - this is the sort of thing that would drive me up the wall :p

---

### Post by kruykaze on 2012-04-23
Not sure why this is marked as solved. But I tried  all the suggestions here and I still ahve this problem.
Any input? Thanks.
Ubuntu 12.04 Beta2 64bit.

---

### Post by vinay_wagh on 2012-04-24
Can admin or the poster remove the [SOLVED] tag... There are many users still having the problem unsolved. 

I tried all the solutions mentioned above with in fact system restart... No effect so far.

-- VInay

---

### Post by vinay_wagh on 2012-04-24
Going through the logs I figured out that the current installed  version (dash-0.5.7-2ubuntu2) has this problem. So how I roll back to the old version of dash? It seems the  dash-0.5.7-2ubuntu1 didnt have any problem. I am not able to see old version(s) in properties tab in synaptic.

-- VInay

---

### Post by montini on 2012-04-24
has everyone tried the solution which helped me?

[http://ubuntuforums.org/showpost.php?p=11800328&postcount=9]("http://ubuntuforums.org/showpost.php?p=11800328&postcount=9")

---

### Post by vinay_wagh on 2012-04-24
I have already tried that... Didnt help me... In fact I forgot to mention for, I am not getting applications tab in dash even under the guest login!

- VInay

---

### Post by montini on 2012-04-24
> **vinay_wagh said:**
> I have already tried that... Didnt help me... In fact I forgot to mention for, I am not getting applications tab in dash even under the guest login!

- VInay

Well, I don't know, maybe You have a different problem then - as in my case guest account didn't show the symptoms - it was OK there. Should I remove [SOLVED] tag anyway?

---

### Post by vinay_wagh on 2012-04-24
@montini:
what is your system and which version of dash are you using?

I have ubuntu 12.04 with all latest updates and dash 0.5.7-2ubuntu2. As mentioned earlier, I noticed that after upgrade from dash 0.5.7-2ubuntu1 to dash 0.5.7-2ubuntu2, the problem started.

So one possible solution I can think of is to roll back to older version of dash. However, I can see that version in synaptic properties tab. So somebody pls tell me how to do that.

-- VInay

---

### Post by montini on 2012-04-24
I'm sorry - I don't remember the version - but I am using the latest precise (12.04) build with updates till today.

---

### Post by montini on 2012-04-24
Oh and BTW - did you try to ```
sudo apt-get remove --purge zeitgeist & sudo apt-get install zeitgeist
```?

---

### Post by vinay_wagh on 2012-04-24
No luck...

-- VInay

---

### Post by montini on 2012-04-24
All right then - I removed the [SOLVED] tag.

---

### Post by larrypg on 2012-04-24
This might not have anything to do with it but just a thought...if you go to system settings,privacy is record activity turned on?

---

### Post by stinkeye on 2012-04-24
I've seen similar issues resolved by deleting 
```
~/.cache/software-center
```

---

### Post by vinay_wagh on 2012-04-26
@larrypg:
I am not able to find "privacy" under system settings.

@stinkeye
Deleting this directories didnt help.

I have already filed this as a bug in Launchpad ([https://bugs.launchpad.net/unity/+bug/987689](https://bugs.launchpad.net/unity/+bug/987689)).

-- VInay

---

### Post by stinkeye on 2012-04-26
> **vinay_wagh said:**
> @larrypg:
I am not able to find "privacy" under system settings.


You should have a privacy setting in System Settings provided by
**activity-log-manager-control-center**

See pic for my zeitgeist related packages.

---

### Post by vinay_wagh on 2012-04-26
I dont have this package installed... 

-- VInay

---

### Post by vinay_wagh on 2012-04-26
I removed (with --purge) and (re)installed the two packages: unity-lens-applications  and unity-lens-music (with related packages). Then the application and  music tabs were restored after the system reboot (logoff is sufficient).


  Thus I feel that these two applications (and unity-lens-video) should  have dependency with dash. Of course it depends on the individual's  point of view. In any case this thing should at least be documented somewhere.
 

@ Others affected by this bug:
Can somebody confirm whether this solution works for you?

 

-- VInay

---

