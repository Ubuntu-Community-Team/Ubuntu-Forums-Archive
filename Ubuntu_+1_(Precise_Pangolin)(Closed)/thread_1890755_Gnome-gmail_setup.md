---
title: "Gnome-gmail setup"
date: 2011-12-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubername on 2011-12-04
Hi

Can anyone help me with gnome-gmail setup please?
I have installed the package and see in the top 'panel', beneath the envelope icon, a 'set up mail..' option, which wasn't there before I installed gnome-gmail, but every time I click on it I simply get a gmail page opening in my browser - it doesn't seem to 'set it up' at all. I would expect it to ask me for the gmail account I would like to use (that's what the various howto's I can find tell me).

Thunderbird is also still the default client whenever I click on  a mailto link, so I have not got it working properly

(Mods - If this is not a Precise Pangolin issue, please move to the right place, thanks)

---

### Post by dsteele on 2011-12-05
In v1.8.2, which is current in Pangolin, gnome-gmail should set itself as the default when you log in. You can try running gnome-gmail to kick the process.

It's possible that gnome-gmail and Thunderbird are battling for dominance - that's kind of the way that GNOME 3 has set things up. If that is the case, uninstall the package you don't want.

If you have an "@gmail.com" address, that is about all you need to do for configuration. The program will launch gmail from the standard browser, which will prompt for credentials, if needed.

If you have a Google Apps account, more configuration options are available from gconf-editor, under apps->gnome-gmail.

When you send a message with an attachment, say from Nautilus or LibreOffice, gnome-gmail will prompt for GMail credentials to access IMAP for the file upload.

---

### Post by ubername on 2011-12-13
I have uninstalled Thunderbird now. I still get the 'Set-up mail' option in the drop down from the envelope symbol, it still opens gmail page, but it doesn't set anything up, and doesn't change the option from the drop down. Part of my problem is that I don't know what should happen, but I would expect the set-up notice to go away and options like'Read mail' 'Send mail' etc. to appear in the drop down

---

