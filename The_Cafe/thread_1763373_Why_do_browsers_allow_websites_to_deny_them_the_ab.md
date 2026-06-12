---
title: "Why do browsers allow websites to deny them the ability to leave a site?"
date: 2011-05-20
forum: The Cafe
---

### Post by itguy1985 on 2011-05-20
I notice when I'm on line, certain websites, or popups, or whatever, will deny the browser the ability to leave. It will ask "Are you sure you want to navigate away from this page?" why would the browser allow this type of activity? Is this bad programing? Are the browser developers just not worried about this type of thing? Are they in on it?. Imo the browser should do what I'm telling it to do, not what the website wants. Why does the website's commands take priority over my own in this situation?  I'm curious to know what you think

---

### Post by lykwydchykyn on 2011-05-20
In a nutshell, we want web applications to be able to act like desktop applications and do all kinds of kewl "web 3.0" type stuff.  In order to make that possible, we have to be able to do things that, unfortunately, can be used maliciously.  That's the double-edged sword of functionality, unfortunately.

You can always use something like "noscript" if you want to guard against it.

---

### Post by dniMretsaM on 2011-05-20
Things like this can be used for good things. Like on a site where your actually doing something productive it will ask you if you're sure you want to leave to make sure that you aren't accidentally trying to close and losing some work. Sadly, this can also be used for not-so-good things and can be very annoying. I think something like Ctrl+Shift+close button that would force it to close and not allow any script to run would be a good thing. I may actually make a request for something like that to Mozilla.

---

### Post by Spice Weasel on 2011-05-20
Firefox actually stops websites from doing this now. If the site spams you with dialogues if you try to quit it will come up with the option "do you want to stop this website from using dialogues?"

E: This post is a complete trainwreck, but I'm too lazy to re-write it. Sorry.

---

### Post by Lucradia on 2011-05-20
> **Spice Weasel said:**
> Firefox actually stops websites from doing this now. If the site spams you with dialogues if you try to quit it will come up with the option "do you want to stop this website from using dialogues?"

+1 to this.

---

### Post by Joe of loath on 2011-05-20
> **Spice Weasel said:**
> Firefox actually stops websites from doing this now. If the site spams you with dialogues if you try to quit it will come up with the option "do you want to stop this website from using dialogues?"

Is this to stop you getting rickrolled? :p

---

### Post by Lucradia on 2011-05-20
> **Joe of loath said:**
> Is this to stop you getting rickrolled? :p

For that, you can do this: [https://addons.mozilla.org/en-us/firefox/addon/youtube-tooltip/](https://addons.mozilla.org/en-us/firefox/addon/youtube-tooltip/)

Install the add-on compat. reporter to install it. It works with Firefox 4. Of course, it only works on youtube.com links, and not youtu.be links (hence why I never click youtu.be links)

---

### Post by coffeecat on 2011-05-20
> **itguy1985 said:**
> I notice when I'm on line, certain websites, or popups, or whatever, will deny the browser the ability to leave. It will ask "Are you sure you want to navigate away from this page?"

When I click on the log out button of this forum, a little window opens asking, "Are you sure you want to log out?"

Is that an example of what you mean? :)

---

### Post by dniMretsaM on 2011-05-20
It's uses the same principle, but it's a different use. It's all based on a javascript alert I believe.

---

### Post by Danny Dubya on 2011-05-20
> **coffeecat said:**
> When I click on the log out button of this forum, a little window opens asking, "Are you sure you want to log out?"

Is that an example of what you mean? :)

That's a fairly tame example -- you logged on by choice and may have accidentally clicked "Log out", so the dialog is reasonable to have.

Something like that doesn't really compare to when some obnoxious, unwanted popup advertisement is unleashed on you, and trying to close it gives you an alert box like the OP is talking about. That's not being helpful, that's downright hostile.

---

### Post by aaaantoine on 2011-05-20
There is a specific set of JavaScript commands for confirming with the user before they navigate away from a page.  I've had to use them at least once, for beneficial purposes.  The browser has a tendency to recognize specifically this type of prompt, and even automatically adds the "Are you sure you want to navigate away from this page?" part of the prompt by itself.

On the subject of Firefox alerts, I love what they've done with them in 4.

1. They're built into the web page, so that they don't prevent you from switching to another tab.
2. They have the "shut it off!!" check box after the second alert appears.

Both are very useful.  And I've found myself sorely needing #2 during development tests. ;)

---

### Post by ki4jgt on 2011-05-20
I got one, in Google Voice (US version) when you're on the phone while checking your email. If you decide you're done checking your email and are still on the phone, it will ask if you're sure you want to close the window. If you click yes. . . It would disconnect your phone call, so that is one place it is needed. :-)

---

### Post by cgroza on 2011-05-20
> **Danny Dubya said:**
> That's a fairly tame example -- you logged on by choice and may have accidentally clicked "Log out", so the dialog is reasonable to have.

Something like that doesn't really compare to when some obnoxious, unwanted popup advertisement is unleashed on you, and trying to close it gives you an alert box like the OP is talking about. That's not being helpful, that's downright hostile.
Or when you click it's close button, it takes you to some other stupid site.

---

