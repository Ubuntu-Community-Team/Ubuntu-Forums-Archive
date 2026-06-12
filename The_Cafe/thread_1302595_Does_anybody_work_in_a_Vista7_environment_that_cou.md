---
title: "Does anybody work in a Vista/7 environment that could help me out?"
date: 2009-10-27
forum: The Cafe
---

### Post by Roasted on 2009-10-27
This is a question coming from a dedicated Ubuntu user who is unfortunately stuck with working in a Windows environment. 

We're all on XP Pro, with intention of moving to Windows 7 eventually. We have many different schools, with different labs, libraries, etc etc etc. So many different configurations it's unreal. As a result, we use default profiles. That way any student who logs in gets the same printers + printer settings, same desktop icons, same everything as the next student.

I failed to get this working in Vista or Windows 7. I have two computers here, one with each OS, and I'm trying to get the default profile working on either one of them.

Has anybody worked in a large Windows environment with Vista or 7 where you've needed default profiles? If so, how did you get them working? I've utilized every resource I know, including calling Microsoft directly (lolol, we're sorry your call has been disconnected after a 30 minute wait).

---

### Post by MasterNetra on 2009-10-27
Might have better luck asking on a Windows Forums ^.^

---

### Post by Johnsie on 2009-10-27
I think it's windows logon scripts you're looking for:

[http://www.computerperformance.co.uk/Logon/logon_scripts.htm](http://www.computerperformance.co.uk/Logon/logon_scripts.htm)

---

### Post by Roasted on 2009-10-27
> **MasterNetra said:**
> Might have better luck asking on a Windows Forums ^.^

I've done that.

I really can't stress how much time I've been googling and how many other school districts I've called to get help from their IT Department.

The problem is, everybody is so comfortable with XP, it's like they'll be fine using XP until year 2055. There's just no documentation out there for what I want to do.

---

### Post by Roasted on 2009-10-27
> **Johnsie said:**
> I think it's windows logon scripts you're looking for:

[http://www.computerperformance.co.uk/Logon/logon_scripts.htm](http://www.computerperformance.co.uk/Logon/logon_scripts.htm)

I'm not too sure... I like the printer-adding thing, but we require specific printer settings to follow down too. The nice thing about profiles is it follows through 100% in each instance. I'm wondering if the logon script would pull the printer preference information down...

---

### Post by Regenweald on 2009-10-27
So you never got it to work with vista ? sorry to hear it. Have you tried contacting MS support directly ?

Edit: just read the entire post, see that you tried already. I'm no help :P

---

### Post by Johnsie on 2009-10-27
A login script can do pretty much whatever you want... However cloning a default profile would probably be a good technique too:

[http://support.microsoft.com/kb/973289](http://support.microsoft.com/kb/973289)

You'd need to create the first account the others would be based on and then use the tutorial above.

---

### Post by Roasted on 2009-10-27
> **Johnsie said:**
> A login script can do pretty much whatever you want... However cloning a default profile would probably be a good technique too:

[http://support.microsoft.com/kb/973289](http://support.microsoft.com/kb/973289)

You'd need to create the first account the others would be based on and then use the tutorial above.

Yeah, I did find that tutorial as well. One question I had was, where in the world do I get the unattend.xml file to even start with?

It's very frustrating, before being able to copy/paste what I needed to get the job done and now I need to use a series of Microsoft bloatware to do such a simple task. Shoot me.

---

### Post by CharlesA on 2009-10-27
Are you guys running a domain using ADDS or something?

I'm trying to remember how they did it at the school I was at. One used a Win2000 AD domain (2003) and the other uses Netware on Win95 machines (1999) *shudder*

I'm not sure how to get it working either, since I haven't actually tried it, and I'm not even sure how you did it in XP.

If you are in a AD domain, I could suggest using group policy, but I don't know how your network is setup.

EDIT:

> **Roasted said:**
> Yeah, I did find that tutorial as well. One question I had was, where in the world do I get the unattend.xml file to even start with?

According to MS you can create the unattend.xml file with WSIM. [quote=MS]You can use the Windows System Image Manager tool to create the Unattend.xml file. The Windows System Image Manager tool is included as part of the Windows Automated Installation Kit (Windows AIK).[/quote]

---

### Post by forrestcupp on 2009-10-27
[Tech-Forums](http://www.tech-forums.net/pc/f9/) has a great Windows forum that I frequent.  There are a lot of good people over there that you will probably have better luck with, since it's a good Windows forum.

If you don't get good help there, try out the proper MSDN forum.  The people there are very quick to help, and it's a massive forum.

---

### Post by Roasted on 2009-10-27
> **forrestcupp said:**
> [Tech-Forums](http://www.tech-forums.net/pc/f9/) has a great Windows forum that I frequent.  There are a lot of good people over there that you will probably have better luck with, since it's a good Windows forum.


Hi there. I'm Jayce from TF. Nice to meet you. :)

---

### Post by forrestcupp on 2009-10-28
> **Roasted said:**
> Hi there. I'm Jayce from TF. Nice to meet you. :)

Nice to meet you.  I'm forrestcupp over there, too.  I haven't had much time to post over there for a while, though.

---

