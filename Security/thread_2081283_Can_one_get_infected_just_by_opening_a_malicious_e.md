---
title: "Can one get infected just by opening a malicious email?"
date: 2012-11-06
forum: Security
---

### Post by arroy_0209 on 2012-11-06
Suppose someone receives an (possibly malicious, user being ignorant of that fact) email in inbox (say in yahoo mail or gmail) and clicks to open it. The content may contain some links to be clicked and may be dangerous; however is it possible to get infected just by opening the email from inbox (without actually clicking any link in the email)? Consider ubuntuOS with firefox as browser with apparmor in use. How about downloading pdf/doc/ppt files and opening them?

Does using thunderbird improve the email related security in any way?

---

### Post by papibe on 2012-11-06
Hi arroy_0209.

Strictly, yes.

However, unless you are being specifically targeted, it is not likely to happen as a random event, as for now, there is no little to none worms/viruses around targeting Linux desktop machines.

This may change in the near future because of Ubuntu/Linux gaining popularity, and also because of the potential games coming to the platform.

Just a few thoughts.
Regards.

---

### Post by mike acker on 2012-11-06
> **papibe said:**
> Hi arroy_0209.

Strictly, yes.

However, unless you are being specifically targeted, it is not likely to happen as a random event, as for now, there is no little to none worms/viruses around targeting Linux desktop machines.

This may change in the near future because of Ubuntu/Linux gaining popularity, and also because of the potential games coming to the platform.

Just a few thoughts.
Regards.

we need more discussion on this.  

you have to be logged in as root to update software, or use sudo. and for sudo you use that from the terminal and you have to give your sudo password.  so this will mean a web page is not likely to alter your installed software.

the thing that remains a question: is what could a bad script do to your browser? particularly could it *** a plug-in to your browser and create a MITM attack ?

that's a concern.  If we put the browser under AppArmor ?  this can restrict what the browser can update, --depending on the apparmor profile.    I'm runnning the profile distributed with 12.04 by Jamie Strandboge of Canonical but I wish I knew more about what it does/does not allow

i use an admin account and a user account. the idea is the admin account has sudo capability; my user account normally won't.

---

### Post by OpSecShellshock on 2012-11-06
> **arroy_0209 said:**
> Suppose someone receives an (possibly malicious, user being ignorant of that fact) email in inbox (say in yahoo mail or gmail) and clicks to open it. The content may contain some links to be clicked and may be dangerous; however is it possible to get infected just by opening the email from inbox (without actually clicking any link in the email)? Consider ubuntuOS with firefox as browser with apparmor in use. How about downloading pdf/doc/ppt files and opening them?

Does using thunderbird improve the email related security in any way?

A lot of web-based email providers allow html code (and the scripts it enables) to be loaded inside a message, so that's one possibility. An email message in the web browser is just like any other web page, with all of the capabilities for unexpected or unintended results that entails. You'd also be vulnerable on the web-based version by allowing ads to load and also allowing images to display. So yes, just reading a message there carries risks, even without following links.

Now, using Ubuntu with Firefox? With NoScript active, you'd have to whitelist the email provider's site in order for it to work, but third party scripts shouldn't run. You can use Adblock Plus to stop advertisements from loading. Actually those two things can be done on any OS. AppArmor can be helpful in stopping directories from being read from/written to, which normally would be allowed since the user who owns those directories is also the user running the browser.

I don't think I would call that state of things infected exactly, since that implies that malware has been installed and has compromised the system, which while technically possible is very unlikely. But there's damage that can be done without installing any software at all.

A mail client like Thunderbird should allow scripts to be blocked, and plain text to be forced instead of allowing html. Check the preferences. Thunderbird can probably be constrained with AppArmor as well, and in some cases I think Thunderbird has been reported as being partially constrained when a profile is enforced for Firefox (that may have been considered a bug and fixed though).

Shorter: yes, malicious code can run inside a web-based email that has been opened and nothing else, provided no measures are taken to prevent such code from running. It probably won't lead to malware installation on Ubuntu. Attachments usually open in whatever application they are supposed to be opened in, so if those applications have vulnerabilities that the attachments are made to exploit, then there is a risk there. Standalone mail clients might make a difference, but I'm not sure how much.

---

### Post by Hungry Man on 2012-11-06
An email can contain images that could be used to exploit the web browser - just today Chrome patched a vulnerability having to do with WebP images.

Emails can also contain attached PDFs, which can exploit browser PDF readers or other readers on the system like Adobe Reader's plugin.

Less likely is a text-based exploit, this is rare and I haven't seen one in years.

---

### Post by offgridguy on 2012-11-06
> **mike acker said:**
> 

i use an admin account and a user account. the idea is the admin account has sudo capability; my user account normally won't.

Could you expand on this please.  I don't totally understand why you would want to do this.   Thank you.

---

