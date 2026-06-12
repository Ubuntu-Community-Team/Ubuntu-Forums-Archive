---
title: "Issue with Lastpass add-on, X and Firefox"
date: 2018-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Godspell on 2018-05-03
I hope I'm in the right place to post this. I'm not looking for a solution, just want to hear other people's thoughts and experience on the matter O:)

I'm on 18.04 and got a bit of a weird one..but there seems to be an issue between Firefox, Lastpass add-on and X.
I have refreshed, removed (--purged) and reinstalled Firefox (and Lastpass) but the issue with Lastpass add-on persists on X -- i.e. not being able to click on the *password* field to login Lastpass. It's really frustrating.

Then, it dawned on me that Ubuntu 17.10 (which is what I was on before) used Wayland by default and it worked so well with my laptop, so I switched to Wayland and et voila, I'm able to use Lastpass without an issue. I don't see how a browser add-on could clash with a display manager..:confused: and I did contact Lastpass support but no reply whatsoever.

Has any of you had this issue?
Also, what are your thoughts on Wayland? A lot of people seem to dislike it..I used 17.10 and Wayland for months on my laptop and didn't have any issue with it.

---

### Post by dunkgreen on 2018-05-03
I had the same problem.  Firefox/Lastpass doesn't work on 18.04 using X.org but with Wayland it's fine.  Thank you for the workaround.

---

### Post by Godspell on 2018-05-03
> **dunkgreen said:**
> I had the same problem.  Firefox/Lastpass doesn't work on 18.04 using X.org but with Wayland it's fine.  Thank you for the workaround.

No probs. I dual-boot Windows and Kubuntu on my main rig...and on Kubuntu (with X11), Lastpass works fine with Firefox...
So, perhaps it's an Ubuntu thing :/

On the flip side, man..Kubuntu looks and feels amazing!

---

### Post by dunkgreen on 2018-05-05
A couple of other points to anyone that finds this thread.  If you still want to use Firefox/Lastpass with X.org then you can choose Create An Account and then the Log In option using the Lastpass Firefox extension.  This will turn on Lastpass through the browser.  I ultimately chose this route since Synaptic does not work with Wayland and I'd rather have than the other issue.

---

### Post by Godspell on 2018-05-05
> **dunkgreen said:**
> If you still want to use Firefox/Lastpass with X.org then you can choose Create An Account and then the Log In option using the **Lastpass Firefox extension**.  This will turn on Lastpass through the browser. 

Oh right, I see what you mean...so logging in through the website switches on (so to speak) the add-on in browser. Good call.

You know, come to think of it, Lastpass and Firefox just don't play nice..

[LIST]
[*]Lately, when I search URL through Lastpass add-on and launch it, it keeps displaying a blank page
[*]On search results, I cannot right-click and *copy **username/copy password* unlike in Chrome
[/LIST]

Lastpass ought to put in more effort to provide smoother user experience in Firefox..it's one of the major browsers afterall.

---

### Post by Godspell on 2018-05-20
Okay, I've found out something else...

When I switched to Ubuntu Communitheme (which looks great btw), this problem goes away. I can now click on Lastpass icon (and the password field) in Firefox in both X11 and Wayland sessions.

Just wanted to share this..

---

