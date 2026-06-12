---
title: "[SOLVED] Automatix for Dapper (5/16/06)"
date: 2006-05-16
forum: The Cafe
---

### Post by arnieboy on 2006-05-16
[http://ubuntuforums.org/showthread.php?t=177646](http://ubuntuforums.org/showthread.php?t=177646)

A beta version of Automatix is out that will work on both Dapper and Breezy. Here is the link to the deb if you are interested in testing this out.

[**Automatix 6.0-5rc4for both Dapper and Breezy**]("http://www.beerorkid.com/arnieboy/automatix_6.0-5rc4_i386.deb")

[B]Please remember: This is a BETA version of automatix. Feel free to try it out on both Breezy and Dapper. If you are using this on Dapper, there is a conflict between zenity and apt that may cause it to crash if you are typing while running Automatix. Avoid typing while using it.

[COLOR="Red"]If you installed Dapper using espresso (Live CD Installer) you will have to reconfigure debconf for all the packages including j2re1.4, Flash and Sun's java.   Open up the terminal and paste or type this command:

```
sudo dpkg-reconfigure debconf
```

Scroll up using the up key to Dialog and hit enter. then you will select ok by hitting Enter. Then scroll down to medium and hit Enter to select it. The utility will then exit on it's own and you can use Automatix as normal.[/COLOR]

People who installed Dapper through the text based installer should not experience this problem. so will not have to do this.[/B]


Post problems or errors on the thread at the link above or join #Automatix on Freenode.net.

We still need programmers who are interested in helping to develop Automatix.

Here is the link to post a feedback form for testing. You can also view previous feedback forms to confirm bugs.

[Automatix Feedback]("http://www.freepgs.com/jasay/Random/automatix/view_feedback.php")

---

### Post by mstlyevil on 2006-05-17
Arnieboy is trying to recruit people to help continue Automatix and make it work on both Dapper and Breezy. 

If you are interested in helping to continue Automatix as a community project please click on the link and join the team. 

The project will need programmers and even testers. It would be really appreciated if people would help continue this great project.

You can click on the link to go to the thread in the Automatix section to post your interested.

 If you are not interested, please refrain from posting your comments in the thread. Start a new thread if you want to just make suggestions for Automatix but do not want to join the team.

Thank you.

---

### Post by mstlyevil on 2006-05-18
There is now a Freenode.net channel for Automatix. This channel is currently for developers and Testers of the development release for both Dapper and Breezy.

The channel will provide support for the general public after Automatix 6.0 is released stable.

If you are testing or helping to develop Automatix 6.0 please join us on the channel so we can produce the best Automatix ever.

The support of this community is greatly appreciated by the Automatix team.

Thank you

#Automatix on Freenode.net

---

### Post by mstlyevil on 2006-05-21
Here is the rundown of what has happened the last few days.

1. Arnieboy has stepped down and has named me the team leader. I will fill that role until a suitable programmer is found to replace me and then I will move to assistant team lead. 

2. We started a cvs based on bzr.

3. Automatix is now registered with Launchpad.

4. The plan is to release Automatix for Dapper as a BETA on the 24th. The Final release is planned for June 1st.

5. A new Automatix project is in the works to move to python. It will be called Automatix2 and it is also registered with Launchpad.

6. The basic structure of the team has been determined. It will take some time to completely organize the team. Here is what we have so far.

mstlyevil-Team Leader
jdong-Co-team Leader,Automatix2 Development Lead
manicka-Advisor 
Zhukov-Lead Programer-Unstable
jaysay-Testing Team Leader
henriquemaia-Translation Team Lead

We still need someone who knows bash and zenity well to come onboard to lead the Stable Support Team. If you are interested in heading up support please contact me.

If you are interested in testing, translating or programing please contact me or the appropiate team leads.

---

### Post by mstlyevil on 2006-05-23
The Beta is out ahead of schedule. WE plan to have the final release ready for June 1. Thank you for all your support fellow ubuntu lovers.

---

### Post by JoWilly on 2006-05-30
Is anything planned for amd64 ?

 It would be nice to have something for that arch, of course with what is available.

---

### Post by mstlyevil on 2006-05-30
[QUOTE=JoWilly]Is anything planned for amd64 ?

 It would be nice to have something for that arch, of course with what is available.[/QUOTE]

Yes, both a AMD64 pure and a AMD64 mixed versions are being worked on as we speak. The AMD64 pure version is up for testing in the Automatix section of this forum.

---

