---
title: "Question about keyloggers"
date: 2012-04-11
forum: Security
---

### Post by bedpotato on 2012-04-11
I wanted to know a bit more about keyloggers. I do not (to my knowledge) have any virus problems, but someone I know does (they use Windows). Hopefully I can persuade them to change to Ubuntu. :)

Here's what I'm trying to find out:

Do keyloggers log *the keys you are typing*, or *the characters those keys are producing*?

Is it recording the fact that you're typing "third row up, fourth from the left" or does it specifically know that you're typing "D"?

I can't seem to find that out by Googling, and I was just wondering if temporarily changing the keyboard settings to a different language when typing in passwords would help prevent keyloggers from capturing your password.

---

### Post by Hungry Man on 2012-04-11
On Windows you can register a key as a hotkey and be alerted every time it's pressed. So the keylogger registers the hotkey and any time I press that key it logs it.

> Do keyloggers log the keys you are typing, or the characters those keys are producing?

Good question.

Because it's handled by Windows and Windows also determines which ascii characters get printed I think it's likely that it's the key being produced.

Therefore typing in another language would not save you.

There are other keylogging methods besides registering a hotkey. By default any program on the computer has read access to the entire computer so it can read any files that may contain passwords.

---

### Post by haqking on 2012-04-11
Depends on the keylogger of which there are many software based and hardware based, some are dumb and some are super intelligent

Some will capture everyting that goes to clipboard and take screenshots and record mouse clicks

If you mean just a straight keylogger then again it depends.

But most keyloggers these days will record what you actually type,

There many ways to fool a keylogger depending on the keylogger of course, things like typing a password in random order by using highlighting and deletion for example, though this technique only fools the reader of the keylogger logs and not the keylogger itself.

The best way is best practices and safe browsing habits to prevent getting a trojan in the first place.

And changing from windows to ubuntu will not prevent keyloggers, there are many for linux, habits are still the main key, if the user habits brought a keylogger to the system in windows then they are likely to experience security issues at some point in Linux also.

Linux does not at this time suffer from viruses the same way but only because there arent any in the wild for linux, trojans and other malware however can still harm Linux if user habits are not improved

Read the link in my signature for the Ubuntu Basic Security Wiki.

Peace

---

### Post by dontquoteme on 2012-04-11
As stated earlier, there are many methods of keylogging - most of those I've seen in action send entire screenshots back - and can be configured to isolate the information that is wanted.  They can email you directly or transmit to a neutral 3rd party server - so that masses of evidence can be collated.

Note: The owner of a pc can legally install a keylogger.  If you're not the  owner you're in dangerous territory if/when it's discovered.

A previous employer wanted to collect evidence on an employee.  So installed keyloggers that transmitted screenshots to a 3rd party central server that they could browse and check what that employee was saying and doing with company computers.   They fired him once they'd collected the evidence.

These are dependent on bandwidth.. if they dial home too frequently or catch too much data, then they're ineffective as the user will detect sluggish response.  If emailing back to the owner is not an option then a hardware keylogger can be used.

Finally a  hardware keylogger fits like a usb to ps2 converter at the back of a keyboard connector.  But you need to have physical access to remove the device to view the data after its collected.  In effect it's just like a usb pen on the back of the keyboard storing data.

These keyloggers aren't dumb... they can be endless configured to store  browsing history rather than just passwords to accounts.  I hope that helps answer your question.

---

### Post by haqking on 2012-04-11
> **dontquoteme said:**
> As stated earlier, there are many methods of keylogging - most of those I've seen in action send entire screenshots back - and can be configured to isolate the information that is wanted.  They can email you directly or transmit to a neutral 3rd party server - so that masses of evidence can be collated.

Note: The owner of a pc can legally install a keylogger.  If you're not the  owner you're in dangerous territory if/when it's discovered.

A previous employer wanted to collect evidence on an employee.  So installed keyloggers that transmitted screenshots to a 3rd party central server that they could browse and check what that employee was saying and doing with company computers.   They fired him once they'd collected the evidence.

These are dependent on bandwidth.. if they dial home too frequently or catch too much data, then they're ineffective as the user will detect sluggish response.  If emailing back to the owner is not an option then a hardware keylogger can be used.

Finally a  hardware keylogger fits like a usb to ps2 converter at the back of a keyboard connector.  But you need to have physical access to remove the device to view the data after its collected.  In effect it's just like a usb pen on the back of the keyboard storing data.

These keyloggers aren't dumb... they can be endless configured to store  browsing history rather than just passwords to accounts.  I hope that helps answer your question.

I agree except for the part about hardware keyloggers.

You dont have to have physical access to get access to the data, i have a few various hardware keyloggers, one has built in wifi similar to this one [http://www.refog.com/hardware-keylogger/wifi.html](http://www.refog.com/hardware-keylogger/wifi.html)

emailing the data back is not limited to software keyloggers.

Peace

---

### Post by woxuxow on 2012-04-11
That's depends on keylogger
I saw a keylogger that register (log) even mouse gesture (in some word mouse hotkey) , mouse key and special character (in win you can keep pressing Alt key and type number like Alt+255)
some keyloggers are too advanced you should be more careful

---

### Post by cariboo on 2012-04-12
If you're curious about how keyloggers work there is one in the repositories, called logkeys, why not install it on your own system, and give it a try.

---

### Post by Hungry Man on 2012-11-18
Good question. On Windows a keylogger can register a hotkey, in that case it's typically going to register 'A' or whatever, and log like that. AFAIK to log this way, globally, requires administrative access. In this case it would naturally be logging the characters themselves.

On Linux, through X keylogging, the keyboard is abstracted via X and input is logged, but not the characters, just the keypresses. Translating isn't difficult as, even if it weren't possible to translate directly, it's a mere shift cipher. It would be very simple to translate but there's probably a simple way, especially since an attacker can create their own input and log that as a 'key' of sorts.

Changing the language probably wouldn't help in either case. Using an onscreen keyboard could, unless they have access to the screen or mouse events.

---

