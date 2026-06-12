---
title: "How do you sign the Ubuntu Code of Conduct?"
date: 2005-12-18
forum: The Cafe
---

### Post by cstudent on 2005-12-18
I got my GPG key generated and uploaded to the server. I've got the key on Launchpad. I go to sign the code of conduct and I read it. Then I get to the next page where it wants me to sign it, but I have no idea what it wants me to enter. Can someone clue me in?

---

### Post by asimon on 2005-12-18
First you have to download the Code of Conduct. There should be somewhere a download link. It's a simple text file. You could also cut&paste it into an editor and save it.

To sign it, call from a command line
```
gpg --clearsign code
```
Use the filename under which you saved the code instead of 'code'.
You have to enter your gpg passphrase. This will generate a file 'code.asc'. This is your signed Code of Conduct.

To upload this 'code.asc' you have to copy&paste the complete text from an editor into the 'Signed Code' text field in launchpad (If I remeber correctly there is no button to upload it with via web browser). Then press "Add" below of the text field.

---

### Post by cstudent on 2005-12-18
Thanks. Got-r-done. I'm now an Ubuntero. :)

---

### Post by bonzodog on 2005-12-18
Same here. Welcome to the ubuntu family!!

---

### Post by itomeshi on 2006-03-17
This is kind of unclear. I think I've figured it out, but can anyone confirm this?

To set up GPG:
1) run 'gpg --gen-key'.
2) run 'gpg --send-key KEYID' where keyid is the 8 character key ID it gave you.

I can't run two because I can't hook up my linux machine to the network I'm currently on (government network thats locked down to known WinXP/2K clients only) :( Is there any way to get around this step?

The next problem is, where do I get the 'fingerprint' to put in the launchpad 'Edit OpenPGP' window?

All I want to do is edit the wiki to add data on my laptop. Sheesh.

---

### Post by John.Michael.Kane on 2006-03-17
I signed the Ubuntu Code of Conduct. 
@itomeshi This should help [https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto).

---

### Post by majikstreet on 2006-03-17
welcome! *laughs evily*

---

### Post by hyperair on 2007-08-06
I've a question.. what's the use of signing the code of conduct?

---

### Post by John.Michael.Kane on 2007-08-06
> **hyperair said:**
> I've a question.. what's the use of signing the code of conduct?

These might help you.
[Code of Conduct]("http://www.ubuntu.com/community/conduct")

[Ubuntu Leadership Code of Conduct]("http://www.ubuntu.com/community/leadership-conduct")

Also signing the Code of Conduct is required for [Ubuntu membership]("https://wiki.ubuntu.com/NewMemberHowto").

---

### Post by gOLdenHaWK3D on 2009-11-03
Read this link - [https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)
It would be great help.

Moreover, the help links are there all over the place. Just follow them & it'll be done :)

---

### Post by FuturePilot on 2009-11-03
This thread is 4 years old...

---

