---
title: "Citrix 23.2.0.10 &quot;App protection&quot; blocks Chrome and Edge from connecting to internet"
date: 2023-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by jajodo on 2023-03-08
Lost a lot of hours on this one so I am posting for others.

I did a fresh install of Ubuntu 22.04 and all was as good an can be expected for a short time.
Then Chrome and Edge stopped connecting to the internet as if a firewall was blocking them.
Interestingly the chromium and firefox snaps were not affected.

I use Citrix to connect to the work network 
On this version number during installation you are asked something like "do you want to use app protection" with little further information.
Who does not want to be protected :)

After days of troubleshooting hardware and vpns and firewalls and reinstalling Ubuntu I isolated the browser problem to clicking yes to this item during installation of Citrix.
Installing Citrix without using app protection causes no problems that I have yet identified.

Hope this saves someone else some days and their marriage.

JD

---

### Post by coffeecat on 2023-03-08
Interesting observation. Since you are not asking for technical help, I've moved this from *General Help* to *Ubuntu, Linux and OS Chat*, where it may give rise to some discussion.

---

### Post by DuckHook on 2023-03-09
I suspect it's another instance of the dumb&#8209;it&#8209;down syndrome at work. Just a guess on my part but I think that the Citrix designers decided that a longer more technical explanation would intimidate their users, so they succumbed to the marketing dodge of stating things "short & sweet; incomplete". Google is another organization that causes no end of trouble doing the same. Every two months, those who must use an app password to sync their 2FA Gmail account with Thunderbird will get a scary message to the effect that they have a potential security exposure. Would they like to enhance their security?

And as you observed, who wouldn't want to do that?

Answering "yes" will delete that app password and cut Thunderbird's Gmail connection.

What's happening behind the scenes is this: Google runs your account through a dumb bot every two months. Among other things, it checks to see if you have any app passwords. If it finds any, then it treats these as guilty until proven innocent.

What they *mean* to say is: "You have app passwords which open potential attack surfaces. Please delete those you are no longer using. As a convenience, we can delete the whole lot of them at once if you click this button."

What they *actually* say is: "Click this button for better security".

I suspect that you dropped down a similar rabbit hole in your Citrix misadventures.

---

### Post by jajodo on 2023-03-10
LOL it seems so.  "App Protection secures corporate data by defending against key logging malware, screenshot malware, and accidental screen sharing. This enables end users to securely access their corporate resources in Citrix Workspace through any device, even one that's unmanaged."

In short.... "NO INTERNET ACCESS, NO THREAT"  :)

---

### Post by DuckHook on 2023-03-10
As an aside, I trust neither Chrome nor Edge because they are owned by monster corporations that have made no secret of their desire to slurp our data for their own nefarious uses. I have no idea what hooks they have coded into their proprietary browsers and don't trust them as far as I can kick them.

Chromium and FF are a different story. Though I wouldn't go so far as to say they are absolutely safe, they are FOSS and therefore open to scrutiny. This forces them to behave.

Hmm&#8230; maybe Citrix is on to something there.

---

