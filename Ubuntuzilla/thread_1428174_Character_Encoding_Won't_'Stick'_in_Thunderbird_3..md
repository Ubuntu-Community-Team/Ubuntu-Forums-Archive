---
title: "Character Encoding Won't 'Stick' in Thunderbird 3.0.3"
date: 2010-03-12
forum: Ubuntuzilla
---

### Post by mlnease on 2010-03-12
Hello,

Just upgraded to Thunderbird 3.03--thanks again, Ubuntuzilla.  One more small hitch I discovered this AM:  Character Encoding (View/Character Encoding) continually reverts to the default, Western (ISO-8859-1).  For proper display I must reset it for every email.

Edit/Preferences/Display/Fonts/Advanced/Character Encodings/Outgoing Mail and /Incoming Mail are both set to Unicode (UTF-8).

Any suggestions?

Thanks in advance.

mike

---

### Post by nanotube on 2010-03-13
hrm, no idea... only thing i can think of is to point you here:
[http://kb.mozillazine.org/Font_settings_in_Thunderbird#Settings_via_the_Options.2FPreferences_dialog](http://kb.mozillazine.org/Font_settings_in_Thunderbird#Settings_via_the_Options.2FPreferences_dialog)

and to suggest that you check if there have been any bugs filed against this upstream (on bugzilla.mozilla.org), and if not - file one :)

---

### Post by mlnease on 2010-03-13
> **nanotube said:**
> hrm, no idea... only thing i can think of is to point you here:
[http://kb.mozillazine.org/Font_settings_in_Thunderbird#Settings_via_the_Options.2FPreferences_dialog](http://kb.mozillazine.org/Font_settings_in_Thunderbird#Settings_via_the_Options.2FPreferences_dialog)

and to suggest that you check if there have been any bugs filed against this upstream (on bugzilla.mozilla.org), and if not - file one :)

Thanks, Nanotube,

I seem to have got it resolved but haven't been able to figure out how.  It wasn't via View/Character Encoding or Edit/Preferences/Display/Fonts/Advanced/Character Encodings; if I can figure out where I fixed it I'll post again in case anyone else has this problem.

Thanks again!

mike

---

### Post by leorolla on 2010-07-15
I got extremely annoyed by this and found the soluion by accident.

You can specify the policy for each folder, and it overrides the Edit->Preferences...

Right-click on the Inbox, go to Properties... and uncheck the Apply default to all messages. 

This should suffice for good messages.

For very bad messages that don't come with the encoding on its headers, Thunderbird will either guess or apply the Default, so you can set the Default to the case that occurs most often in very bad messages. Probably it won't be UTF-8 anyway [;)]

---

