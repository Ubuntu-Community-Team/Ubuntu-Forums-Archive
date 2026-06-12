---
title: "Did I open up my server?"
date: 2010-07-25
forum: Security
---

### Post by oomar on 2010-07-25
OK so in a moment of idiocy I decided to run a privilege escalation script on my server to see if it would actually work. Well, good news, it didn't. Of course now I'm wondering if it potentially opened up any security holes or modified something in the process. Now of course I looked through the code and modified it so that I thought it would work. it looks like it didnt work because one of the commands being run in the script isnt installed on my system. 

I did double check the authorized_keys file and found 1 key that I didnt know where it was from. of course that could potentially just be me forgetting it. OR it could be the key generated from the exploit. 

uhhh I can provide more information as needed. 

the exploit is from inj3ct0r found [here]("http://inj3ct0r.com/exploits/13209").

if someone could take a look at this and see if there is anything that I should be worried about I'd be very grateful.

Oh and it uses SSH to localhost and I, of course, am running SSH on a non-standard port so I took that into account... idk. let me know if you see anything.

Thanks

EDIT: # Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

also is there any particular reason I need PAM? I'm not really sure what it is for.

---

### Post by jaakan on 2010-07-25
> **oomar said:**
> OK so in a moment of idiocy I decided to run a privilege escalation script on my server to see if it would actually work. Well, good news, it didn't. Of course now I'm wondering if it potentially opened up any security holes or modified something in the process. Now of course I looked through the code and modified it so that I thought it would work. it looks like it didnt work because one of the commands being run in the script isnt installed on my system. 

I did double check the authorized_keys file and found 1 key that I didnt know where it was from. of course that could potentially just be me forgetting it. OR it could be the key generated from the exploit. 

uhhh I can provide more information as needed. 

the exploit is from inj3ct0r found [here]("http://inj3ct0r.com/exploits/13209").

if someone could take a look at this and see if there is anything that I should be worried about I'd be very grateful.

Oh and it uses SSH to localhost and I, of course, am running SSH on a non-standard port so I took that into account... idk. let me know if you see anything.

Thanks

EDIT: # Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

also is there any particular reason I need PAM? I'm not really sure what it is for.

the script creates a new key and PAM is for Authentication.

if your worried you can always wipe-out your keys and create new ones.

remove that new key and in the future look over scripts before you run them, so you have an idea of what they could do.

---

### Post by oomar on 2010-07-25
I did look over it. I was just short-sighted enough to not run it on a different system than one i actually use.

I deleted the only other key i didnt recognize as one was from my laptop and the other my ipod. and I knew it created one, i just wasnt sure if it deleted it after, because if it did, that wouldnt explain its presence

and I know PAM is for authentication but how? is it a separate implementation? I use SSH keys to log in from my laptop and ipod... is PAM authentication a part of that process? What I'm asking is would it disrupt anything if i disabled it.

Thanks for the response

---

