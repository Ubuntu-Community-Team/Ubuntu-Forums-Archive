---
title: "Opinion on GPG-Agent"
date: 2014-12-22
forum: Security
---

### Post by kevdog on 2014-12-22
I really don't use any gpg-agents historically, however now I'm in need of a gpg-agent solution for a process that automatically makes an encrypted offsite backup utilizing gpg keys using ssh(sftp) for the transfer of files.  I've read gpg-agent can handle both ssh and gpg keys so that probably is the utility I'm going to utilize. 

I tried numerous configuations, however what I'm in need of is a solution that would ultimately require the least amount of typing of passwords. So basically I need a front-end to the gpg-client.  I'd ideally like the agent to be loaded with the keys upon startup if possible so I can guarantee the gpg-agent is filled.  The front-ends I've tried are envoy, keychain, and kwallet via the ksshaskpass executable.  Ideally I'd like a master keychain to be unlocked upon login with and within the keychain are the various ssh and gpg keys with their stored password.  This would require me to only type on password which would then unlock the master keychain with the front-end then responsible for loading of the keys into the respective agent. The only problem I have with a solution like keychain is I believe it would require that for each key loaded, a password would need to be typed.  I'm assuming my solution would require either use of the gnome-keyring or something like kwallet.  I'm open to any other solution as well.

---

### Post by bashiergui on 2014-12-22
This sounds exactly like what you're describing, and it's automagic. [https://www.digitalocean.com/community/tutorials/how-to-use-duplicity-with-gpg-to-securely-automate-backups-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-use-duplicity-with-gpg-to-securely-automate-backups-on-ubuntu) 
Of course that tutorial is for 12.04 but I'm sure it's adaptable.

---

### Post by kevdog on 2014-12-22
That link: [https://www.digitalocean.com/communi...kups-on-ubuntu](https://www.digitalocean.com/communi...kups-on-ubuntu) isnt going to work very well.  It just puts the passphrase in a file.  I specifically need some agent solution for the password.

---

### Post by bashiergui on 2014-12-29
Curious if you found a solution. Any luck? 

I'm assuming you want a FOSS solution? I'm guessing commercial options like Powerbroker would be able to manage it but for a pretty penny.

---

