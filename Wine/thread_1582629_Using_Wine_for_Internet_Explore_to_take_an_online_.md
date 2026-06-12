---
title: "Using Wine for Internet Explore to take an online course exam?"
date: 2010-09-26
forum: Wine
---

### Post by M4570D0N on 2010-09-26
I apologize if this has been covered numerous times already. I have been searching for a while and not finding a direct answer.

I am taking an online graduate course this semester. I can access the course website and material with Linux/Firefox without any problems. However, the professor has stated that we are required to use Internet Explore on a Microsoft OS to take the exams.

I asked him why that is, and here is what he told me:

[quote=me]Dr. Bob,
I am currently running Linux Mint 9, which is based on the Ubuntu 10.04 OS, with Firefox 3.6.10. I can still dual boot into Windows 7 if I really have to, but after repartitioning to allocate more space to my Linux OS, Win 7 is rather slow and annoying. What are the particular reasons why the practice exams/exams must be taken with a Windows OS using Internet Explore? I'm really not a fan of using either when at all possible.[/quote]

[QUOTE=Dr. Bob]In short, every browser (and OS) has particular limitations with regard to exam security. The Firefox browser will not allow me to do certain things related to exam security. It has to do with their "philosophy." The Mac OS separates windows and menus, which makes exam security impossible (without a lockdown browser). In addition, the amount of work to customize the exam tool for every browser would be huge (although I would extend it to Firefox if they would allow certain things ...). Since IE is the default browser on PCs and has the highest usage, it makes sense to use it (as opposed to any other alternative).

I have considered moving to a "lockdown browser" exam tool that would work on all browsers and OS's. But when I surveyed students about it the results were about 98% negative. Only the Mac and Linux users were positive. So making 2% happy at the expense of 98% doesn't look too promising.[/QUOTE]

[QUOTE=me]Thanks you for the info. I assume that the same, or similar, security limitation issues with Firefox also exist with Google Chrome or Opera?[/QUOTE]

[QUOTE=Dr. Bob]Chrome is similar to Safari. Both are based on the old KHTML rendering engine. I'm not sure about Opera. That browser has had a longer development, so they are probably doing their own thing.

The security issue is more of a "philosophy" issue in what browsers will allow the developer to do. For example, IE might require that the user allow something. Apple and Netscape feel that the typical user does not know enough to make a choice, so they will just completely disallow a feature. Obviously, the point at which disallowed features becomes overbearing is debatable.

As it stands now, creating a secure (in terms of securing the exam data) exam environment would require a lockdown browser for Firefox, Safari, and Chrome (and anything on the Mac). I am not sure about Opera.[/QUOTE]


For some reason, it did not occur to me at the time to ask him about using IE on Linux through Wine (or Winetrick?). I don't know when I'll be able to talk to him some more this week (or if he is very knowledgeable about Wine or Winetricks in particular), but with my first exam coming up in a couple days I thought I might ask here. 

I'll probably have to just dual boot into Windows for this first exam, but it would be a whole lot less of a hassle if I could open IE through Wine with all of the security related features I would need to satisfy his exam environment requirements. I'm not looking to try get around any security features. The exact opposite, actually. My biggest concern is if I used wine and was able to get access to the exam, but did not have some feature enabled, or something that conflicted with the monitoring, and then get accused of academic dishonesty for attempting to "cheat." I have zero desire to risk getting a zero for the class and/or face the possibility of expulsion from grad school just because I didn't want to boot into Windows.

I'm still a GNU/Linux n00b and and I've honestly never used Wine up to this point, so I am really not familiar with the differences between Wine's implementation of IE and actually running IE on Windows, from a security features standpoint.

Any assistance is very much appreciated.

---

### Post by Dayofswords on 2010-09-26
> The security issue is more of a "philosophy" issue in what browsers will allow the developer to do. For example, IE might require that the user allow something. Apple and Netscape feel that the typical user does not know enough to make a choice, so they will just completely disallow a feature. Obviously, the point at which disallowed features becomes overbearing is debatable.


I wonder that thing Mr.Bob is talking about...

---

### Post by teh603 on 2010-09-27
He's concerned about people changing to another browser tab/window and googling for the answer, or so it seems. That's generally the issue with "exam security," at least as far as the school district I work for is concerned. Ultimately, he wants to make sure the only thing working on your computer is his exam.

---

### Post by SeijiSensei on 2010-09-27
That seems rather ludicrous if true.  Why can't I open another browser?  Run a virtual machine and open another browser there?  Use wget from a command prompt?  Hell, there's always the option of having another computer sitting next to me during the exam.  I don't see how you can really enforce any kind of exam security in a remote, online setting.

---

### Post by M4570D0N on 2010-10-18
Sorry I didn't get back to this earlier. Interestingly enough, opening another browser like Firefox, or even another tab to access Google is not an issue. Someone else in the class asked him about this as well.

[QUOTE=some student]Hi Professor Dr Bob,

I just took the practice exam 1 and I have some concerns.
...
2) Is it permitted to google the terms of question in the exam?
3) It looks like I can not access to online courseware and the exam at the same time in MSIE. Is it ok to browse courseware content in Firefox while taking an exam in MSIE ?
4) The help page was poped up several times when I was trying to edit what I was writing in the essay question. What kind of problem is that?

Thanks,

some student[/QUOTE]

[QUOTE=Dr. Bob]...

2. If you have to do that you will probably run out of time. Remember that the exams have time limits.

3. You can browse the courseware. Again, remember that the exams have time limits.

4.  You cannot use function and/or various key combinations on the exam. If  you do, you will see the display switch to the help page (in some  cases). You can return to the edit page by using the top-right menu[/QUOTE]

#4 was referring to the fact that ctrl+c ctrl+v ctrl+f and so on, are disabled.

He advises against googling due to time constraints, but  it is not prohibited. 

I tried to set up IE6 and IE8 through winetricks, but both resulted in an extremely buggy browser that was pretty much useless. If I tried to go to Internet Options, it would crash the browser every time. When I tried to log in to my class' courseware, the login link that is supposed to bring up the window to input my info does nothing. Clicking any link that results in something popping up did nothing, even right-clicking on the page or a link and clicking new window/open in new window. 

At this point I'm about to just give up since the class will only be for another 2 months. How much time/effort would I have to put into setting up Virtualbox on Maverick to run Windows 7? Can I set it up so that it is basically a clone of my current Windows 7 partition, or would I be required to essentially start from scratch?

---

### Post by cogadh on 2010-10-19
Internet Explorer on Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

As you can see, it pretty much doesn't work. However, you might have some success if you try IEs4Linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

