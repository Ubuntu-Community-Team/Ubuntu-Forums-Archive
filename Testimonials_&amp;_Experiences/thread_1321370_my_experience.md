---
title: "my experience"
date: 2009-11-10
forum: Testimonials &amp; Experiences
---

### Post by mattsegstro on 2009-11-10
I created a post a number of days ago in the General Help section about the program built into Ubuntu 9.10 called Computer Janitor.  After getting my question answered, I ran into some trouble and thought I would post in here what I just posted in that thread.  I figured that I would maybe have a better chance of reaching people if I post in Testimonials and Experiences rather than General Help.  The people I want to reach are those who participate in developing these programs, mainly the program available for download through the Ubuntu software center called Bleachbit.  So enough of an introduction, here is a slightly edited version of what I posted elsewhere.

I needed to send some emails after running all those things like Synaptic and Bleachbit, and was dismayed when my contacts were gone. Either Bleachbit or Synaptic deleted all my contacts in Evolution. I'm not exactly sure what else it has done as I haven't really had a chance to do much else, but surprisingly, when I tried to log back into the forums, it had my password saved still. It didn't automatically keep me logged in so it did remove something, but yet it kept the information behind in Firefox. In Bleachbit I selected everything so that it would remove as much as possible (but either I'm stupid or it didn't ask me about Evolution contacts!). So it just baffles me as to why this program would remove something as obviously useful as my contacts list, which it has absolutely no reason to clean out, and yet keep my saved passwords in Firefox.

Again let me say that I'm not posting to get mad at any of you for the suggestions you made, I'm simply posting this so that maybe someone looking around here will not make the same mistake I made and will leave these things alone in the future. Bleachbit is not worth running. Ever. Obviously, as other posters have said, neither is Computer Janitor, and while I'm pretty sure that the cleaning Synpatic did wasn't to blame for my problems, that's probably best left alone as well. I'm not sure why a program would be created to do such stupid tasks, but it is certainly not worth anyone's time to run or bandwidth to download.

Sorry if I'm ranting here, I have just been on "cloud 9" ever since starting to run 9.10 the day it came out. I loved every minute of it, I thought it was the greatest thing ever and now I'm faced with this. This is not a big enough issue for me to stop using Ubuntu but I really am disappointed that these things can happen and that no warnings are given. Running Bleachbit it warned me that a certain option would remove all my bookmarks (I don't have any so it didn't bother me), but why couldn't such a warning have been given that "selecting this will remove all your contacts" or something like that? While it's not a big issue for someone like me with just about nothing to lose in testing these kinds of programs out on my system (I haven't lost anything at all in fact other than time), for someone who has a lot to lose this could turn them off from Linux altogether. Or for someone who is simply trying Linux out of curiosity rather than a deep rooted hatred for Windows like I have, this could cause them to go back to Windows. The reason why I'm sticking with Ubuntu is because I'm waiting for Mint to release a new version this month, and for Mepis and PCLinuxOS to release versions with the updated KDE4 in the future for me to try out, and I'm desperate to not need to go back to Windows. But for someone else, this could turn them off altogether and Linux doesn't need that right now.

People, learn to write programs that do what we want them to do and don't do what we don't want them to do. For example, for the Windows users out there, I used to always run CCleaner. I never once used it's built in backup function for registry edits and always ignored it's warnings about cleaning because it did what I asked it to and nothing more. Bleachbit didn't do what I asked it to do, and instead did what I didn't ask it to. Please write better programs!

OK my rant is done, sorry for this being so long, I'm just really frustrated now.

---

### Post by jdrodrig on 2009-11-10
I find the search function of these forums quite powerful and fast, so no need to worry about in which subforums your posting is; it will get found.

But I guess it wouldnot hurt to *tag* your posting with keywords.

---

### Post by HappyFeet on 2009-11-10
```
sudo apt-get clean && sudo apt-get autoremove
```
will work just fine. Try it.

---

### Post by solwic on 2009-11-10
> **HappyFeet said:**
> ```
sudo apt-get clean && sudo apt-get autoremove
```
will work just fine. Try it.

What does apt-get clean do?

---

### Post by HappyFeet on 2009-11-10
> **solwic said:**
> What does apt-get clean do?

When you install applications, the .deb files go into /var/cache/apt/archives/. They will stay there until you do apt-get clean. Plus, if you do not do this, reinstalling an application will only reinstall the .debs already on your system. So, if they are corrupted...you get the idea. Autoremove removes unused system files that are left behind after you uninstall something.

---

### Post by mattsegstro on 2009-11-10
Thank-you for the replies and the advice, after posting that I just went to bed and I'm not so annoyed today!  I wasn't sure what Bleachbit and all that did and so I just threw in the Ubuntu disk again and reinstalled it.  It hasn't lost me anything except time so I'm not even all that annoyed about that.  It's a learning experience I guess, I just know, and I hope other people now know, to leave something like Bleachbit alone, and maybe use those commands to autoremove or clean or whatever, but I think for me at this point I'm just going to leave things alone, if I start having problems I can try some of those things or post my problems in the forums and get it answered that way but I'm pretty sure that Ubuntu isn't the same as Windows in that you have to constantly keep on top of things like degragging, registry cleaning, junk files cleaning, malware scanning etc.  In fact, if I'm not mistaken defragging can't really even be done in Linux, there isn't a registry either, and we all know about the malware situation.  If I'm wrong about those then please correct me but unless I hear something otherwise I'll try and sit back and relax and just not worry about these things anymore!

---

### Post by Irihapeti on 2009-11-10
If Bleachbit is misbehaving, then its developers might like to know. It could be worth reporting your experience to them.

As I understand it, fragmentation isn't the problem in Linux that it is in Windows. Instead of a registry, there are all those config files in /etc, and in your home directory, which are at least easier to get at and read (and remove) if necessary.

My son had been a serious user of Ccleaner and similar utilities when he was using Windows (so was I, actually). It took him a little while to get used to the idea that Linux didn't need this kind of thing. So I can understand where you are coming from.

---

### Post by cariboo on 2009-11-10
I have to agree with Irihapeti, the forums are the wrong place to post what you think are maybe bugs. Create a [Launchpad ]("https://launchpad.net/") account, and when you encounter a bug, report it. To report a bug Press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

for example:

```
ubuntu-bug bleachbit
```

Then follow it up with any comments you have. Open source counts on everyone helping to get rid of bugs and to make the programs better.

---

### Post by mattsegstro on 2009-11-10
I was actually just on the Bleachbit site reporting the bug when Evolution told me that you had replied to the thread.  I have a launchpad account and so I will try and be diligent about reporting bugs, I guess I have to try and have a better attitude though when reporting them and not be angry because that doesn't help anyone! lol

And yes, I think a lot of Windows converts find it takes a bit of getting used to, not needing to use CCleaner (I was a huge fan too!), not needing to use any of that... but don't you agree that the freedom from those programs is fantastic!?

---

### Post by solwic on 2009-11-10
> **HappyFeet said:**
> When you install applications, the .deb files go into /var/cache/apt/archives/. They will stay there until you do apt-get clean. Plus, if you do not do this, reinstalling an application will only reinstall the .debs already on your system. So, if they are corrupted...you get the idea. Autoremove removes unused system files that are left behind after you uninstall something.

Thanks.  I knew about autoremove, but had no idea about the other.  

Sorry for hijacking the thread there for a minute.  :biggrin:

---

### Post by HappyFeet on 2009-11-10
One other thing, you should always do:
```
sudo apt-get clean && sudo apt-get autoremove
``` 
after you uninstall something. That way, when you reinstall it, you are assured of fresh files.

---

### Post by running_rabbit07 on 2009-11-10
> **HappyFeet said:**
> One other thing, you should always do:
```
sudo apt-get clean && sudo apt-get autoremove
```after you uninstall something. That way, when you reinstall it, you are assured of fresh files.

I didn't know about that. Do you have Lucid yet?

---

### Post by HappyFeet on 2009-11-10
> **running_rabbit07 said:**
> I didn't know about that. Do you have Lucid yet?

Nah, I'm going to wait a little bit before I start testing.

---

### Post by running_rabbit07 on 2009-11-10
> **HappyFeet said:**
> Nah, I'm going to wait a little bit before I start testing.

It was the fastest upgrade and no problems, lol.

---

### Post by pataphysicianu on 2009-11-10
Were your contacts in evolution actually local, or do you have a link to online google contacts, or exchange server contacts?

Online evolution contacts like google's or exchange are just put into the cache, if the cache is wiped out, it just gets them from the online service again, but only if your online and logged in. Bleachbit will delete this file, but it is no big deal as all these contacts are actually online somewhere. there is a setting when you set up google or exchange contacts to also copy them to you local contact repository, these files are untouched by Bleachbit.

My guess is you set up online contacts and then Bleachbit cleared the cache, then you opened up evolution when you were not online, so evolution couldn't grab the contacts from online, and so showed nothing.

---

### Post by mattsegstro on 2009-11-10
I'm not exactly sure about whether the contacts were local or online actually.  When I first got 9.10 I created an account with launchpad to get access to that Ubuntu One thing, that 2GB of cloud storage, and so I think it was in that cloud actually.  However, when I logged into the cloud there were no contacts stored in there so maybe it was stored locally.

Either way, I'm always online, wired connection that hasn't been down recently as far as I can tell, and certainly wasn't down when I was having problems last night as I was logged into Facebook and chatting with people while I was trying to locate my contacts (and Facebook doesn't take enough of my bandwidth to prevent Evolution from accessing the cloud account either).  So either they were stored locally and Bleachbit shouldn't have touched them, or they were stored online and Bleachbit did something to them because there's none there, I had to export my contacts list from my Gmail account again today and import it back into Evolution.

But your idea does make sense, I hadn't thought of that as a possibility.  I will come back to this thread and the thread I created in the general help category and post whatever response I get from Bleachbit since I posted the bug today on their site.

One other thing, on the topic of Lucid, at what point would it be useful for someone like me to upgrade to it?  Someone like me meaning someone who doesn't mind if something breaks my system occasionally since I have a backup laptop that I can use in a pinch if I have to accomplish something quickly.  So I don't mind it if my system breaks occasionally, but I don't have much CL experience so if a problem comes up I can't really fix it myself or anything.  Should I wait for a certain alpha release or a beta release or just wait till the full version comes out?  And if I wanted to upgrade, how would I go about doing it?  But basically I guess the reason I'm asking is because I do 99% of my computing in a browser.  Google Docs for school assignments, Gmail for email (I just started using Evolution like a week ago) so basically I don't have all that many needs in terms of what's on my system but I would be interested in just checking out newer versions of Ubuntu just for the heck of it, and I certainly wouldn't mind getting more involved in bug posting... like I said I can't fix problems myself but I can easily run a system and find bugs.

I hope from that you can tell what kind of a computer user I am and maybe offer some advice on when to upgrade!

---

