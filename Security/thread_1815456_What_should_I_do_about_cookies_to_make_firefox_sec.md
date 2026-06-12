---
title: "What should I do about cookies to make firefox secure?"
date: 2011-07-31
forum: Security
---

### Post by arroy_0209 on 2011-07-31
1. What should be "privacy" settings for a more secure firefox 3.6.18, in ubuntu 10.04 LTS. Should one choose "never remember history" or  "use custom setting for history". In case I choose the later, what should be cookies settings: accept cookies (y/n), accept third party cookies (y/n), keep until (I close firefox) (y/n), automatically start firefox in a private browsing session (y/n).  2. This is related to above issues. In case I try the option "never remember history", I will have to enter web address every time I start firefox and I will have to give my login name for various sites each time. This is annoying. So should I rather try custom setting for history? I am ready to have this annoying feature in order to make the browser more secure. I am not sure what harm cookies can do in ubuntu.

---

### Post by lovinglinux on 2011-07-31
The only issues with cookies that I am aware are those related to privacy, because the can be used to track your browsing habits. Unfortunately, if you don't allow cookies, sometimes even third-party ones, you can lose a lot of the web site functionality.

I have tried many different approaches in the past. Currently, I use Custom settings for History, allowing all cookies and keeping them until they expire. However, I also set the option to "Clear history when Firefox closes" and include cookies in the list. This creates an annoying problem, because it deletes authentication cookies that I need to login automatically on sites I have accounts and visit frequently. To solve this problem, I use [Biscuit]("https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/") extension, which allows to select which cookies you want to preserve, so they are not deleted when Firefox closes.

I also use [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/") an AdBlock Plus, which block many sites and thus prevent them from creating cookies on my machine.

What you should really be worried about are the flash cookies. For that, use [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/") extension.

I also use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/flashblock/"), to deal with flash performance issues, but it also prevents flash objects from creating flash cookies.

---

### Post by bodhi.zazen on 2011-08-01
Personally I use NoScript and BetterPrivacy and allow JS and cookies only from trusted sites.

Any other sites I either do not visit or only allow temp cookies, clear all cookies at the end of the session.

---

### Post by whatthefunk on 2011-08-01
I only allow cookies from sites that I trust.  I dont clear at the end of each session because most sites need cookies to auto log-in and I cant be bothered to log-in everywhere all the time.  I clear history after each session.  I have saved all the sites that I normally visit as bookmarks and tweaked the urlbar settings so that only bookmarks are displayed in the drop down menu.  This way, I can easily get to all my most used sites without having to type the whole web address.  I also use NoScript.  Ive never had a security problem with Firefox and the way I have it is convenient for me.

---

### Post by lovinglinux on 2011-08-01
> **whatthefunk said:**
> I only allow cookies from sites that I trust.  I dont clear at the end of each session because most sites need cookies to auto log-in and I cant be bothered to log-in everywhere all the time.  I clear history after each session.  I have saved all the sites that I normally visit as bookmarks and tweaked the urlbar settings so that only bookmarks are displayed in the drop down menu.  This way, I can easily get to all my most used sites without having to type the whole web address.  I also use NoScript.  Ive never had a security problem with Firefox and the way I have it is convenient for me.

An alternative to be able to clear all cookies on exit is to use [Secure Login]("https://addons.mozilla.org/en-US/firefox/addon/4429/") extension. It allows to safely store bookmarks that automatically log you in.

---

