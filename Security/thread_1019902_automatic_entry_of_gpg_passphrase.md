---
title: "automatic entry of gpg passphrase"
date: 2008-12-23
forum: Security
---

### Post by scarf on 2008-12-23
thank you for your consideration but please spare me the lectures on why this is insecure, i have heard it all and understand your point, but you are not in my situation.  let's just focus on a solution. ;)

i am mainly using gpg with thunderbird for encrypting/signing e-mail, via the enigmail plugin.

in windows xp i was able to use the gpg option '--passphrase-file <filename>' to define a file with the passphrase contained in it.  this way, the passphrase was automatically read and i did not need to type it.  now, in ubuntu, that option doesn't seem to have any effect, as i am asked for the passphrase.

now i understand i am using a more secure environment than windows xp, so this may be a little harder to get working.  but, keep in mind that '--passphrase-file' is a valid option and should be able to work.  however, maybe some other things need to be adjusted/configured, like gpg-agent or something to handle the passphrase instead....

please let me know.

---

### Post by scarf on 2009-01-06
bump

---

### Post by Dr Small on 2009-01-06
Why doesn't the --passphrase-file option work? I have never tried it, but it should work if the path to the file is correct, and the permisions are set so you can read the file.

---

### Post by kevdog on 2009-01-07
Could you provide an example of your command line syntax and provide the permissions (ls -la) of the passphrase file?

---

### Post by scarf on 2009-01-10
this is what i can see enigmail doing by looking at the openpgp console:

```

/usr/bin/gpg --charset utf8 --passphrase-file /full/path/to/file --batch --no-tty --status-fd 2 -d --use-agent

```

i also have the enigmail option "never ask for any passphrase" checked.

i am still prompted for the passphrase.

permissions of the passphrase-file are 600 (-rw-------)

---

### Post by scarf on 2009-01-11
i think the issue here is seahorse is intercepting the passphrase request from gpg.  i have loaded password and encryption settings (system > preferences) and i told it to remember the passphrase and show the icon, etc.

i tried using enigmail and typed in my passphrase once, and now i see the keys icon down in the notification area, indicating it's remembered my passphrase.  so this is kind of along the lines of what gpg option --passphrase-file will do, but not quite.

i have loaded seahorse (accessories > passwords and encryption keys) and i see, on the passwords tab, that it has my GPG key passphrase remembered there.

if we can get seahorse to permanently remember my passphrase, that would be acceptable.  it would need to remember it after reboots, etc.  i see that it has wifi passwords also stored in there, which are remembered after reboots, so perhaps this is possible?

---

### Post by kevdog on 2009-01-11
I wish I could help you but I don't run seahorse, but rather firegpg/gmail as my GUI interface to gpg, or simply run gpg on the command line by itself.

---

### Post by argie on 2009-01-11
Is this still a problem? In Ubuntu 8.04, I would just set "Always remember passphrases whenever logged in" in System » Preferences » Encryption and Keyrings » PGP Passphrases

---

### Post by scarf on 2009-01-11
i don't think it's a problem now, as i have rebooted and tried to sign an e-mail.  a box popped up saying the passphrase was cached, and i authorized its use, then the keys showed up in the notification area.

apparently the settings i have explained in my previous post do the trick.  but, i was messing around with other things like gnupg-agent, pinentry, gpg-agent.conf (i've uninstalled or deleted all those now), etc.  so i'll watch this for a while just in case.


update: after a few reboots, my passphrase is still remembered and i do not have type it!  wonderful!  note that i am also using the enigmail plugin from the repositories, not downloaded from mozilla.org, so that may help in making this work.

---

### Post by wdaniels on 2011-05-23
I came across this thread searching for a reason why --passphrase-file didn't seem to work. I was using gpg via command line, not in conjunction with enigmail, but it kept complaining that gpg-agent was "not running in this session" then prompted for a passphrase. Adding --batch just caused it to fail with "invalid passphrase".

Eventually I realised that you need to add --no-use-agent to stop it trying to read the passphrase from GnuPG-Agent. The documentation suggests that it will simply try the agent first, but actually if it fails there it doesn't seem to bother looking for the file and just prompts.

This was on Ubuntu 10.04 gpg version 1.4.10 so maybe it is fixed already...I'll try to remember to check. Possibly it is intended behaviour anyway, though I think the documentation should be clearer if that is the case.

So I'm just documenting my findings here in case anybody else searches for the same problem, even though the OP has solved his issue. I don't know if enigmail has a way to edit that command line, but changing it to --no-use-agent instead of --use-agent I guess would have done the trick.

---

### Post by newalexandria on 2012-04-18
We are experiencing the same problem, using gpgme with rails app on a production environment.  I'll follow-up here if we can make headway with these idea.  

(posting now really just to bump)

---

### Post by keirvt on 2012-10-11
Each year I am delivered thousands of encrypted files all with the same pass phrase to decrypt and place in a directory for reading into a database.

I am using Redhat Santiago 6.3 (regularly patched and updated) 
This year  gpg started insisting that a passphrase be entered for each file.

After taking clues from previous posting on this thread I found this works

gpg --batch --passphrase-file /home/passphrasefile -d gpgEncrptedFile  > decrypted

---

