---
title: "Encryptfs, PAM and OpenSSH sftp-only option"
date: 2013-02-23
forum: Security
---

### Post by kevdog on 2013-02-23
I didn't encrypt the individual /home directory during setup by default, rather later added the encryptfs and added a .Private file within each user directory.  ~/.Private is mounted as ~/Private --- This is standard convention.

I later altered the PAM module to auto-mount the ~/.Private encryptfs upon login -- either shell, or ssh.  This process works really great.  This was by virtue of use of the eCryptfs module and then encryptfs-utils package.

Is I setup an ssh user that is internally restricted to sftp-only (as configured within the sshd_config file), will the ~/.Private directory continue to be auto-mounted, or do I need or further more comprehensive option such as setting up a full SSH Jail or use rssh?

Hopefully that made sense.

Just some background.  I trying to allow remote users to backup their data to my server.  My requirements are that I want the users data to be encrypted, for the sync process to traverse a secure tunnel, and for the encrypted files on the server to be actually in some type of encrypted container, so other users couldn't see the file names of the encrypted files.  Although this is still in the planning phases my plan is as follows:

1. iptables configuration/portknocker to shield listening port of openssh server
2. Use of the program duplicity (which is backend of Deja Dup), that allows for creation of gpg encrypted gzip files and also allows for creation of incremental of rdiff backups to save space.
3. Use of quota that prevents my server's hard drive from becoming full as a user tries to commando the space.
4. Use of either rsync, sftp, or sshfs to provide the secure tunnel (yes I'm aware this is really all provided by the OpenSSH package).
5. Use of encrypted container on the server - As presented above I'm really thinking about the use of encryptfs to provide this container although I am aware of other options.
6. Ideally automounting of this encrypted filesystem on the server
7. Restricting the actual user or limiting the actual login user to the least amount of services on the server machine -- either through a formal SSH jail, limited ssh jail (rssh), or easy internal-sftp only.  I've never set up a formal jail before.  Obviously use of OpenSSH's internal-sftp only option is very easy to set up, however I don't know if I choose to employ an encryptfs, if this would automount upon login.

I'm definitely open to further suggestions or experiences from others.

---

### Post by Ms. Daisy on 2013-02-23
> Just some background. I trying to allow remote users to backup their data to my server. My requirements are that I want the users data to be encrypted, for the sync process to traverse a secure tunnel, and for the encrypted files on the server to be actually in some type of encrypted container, so other users couldn't see the file names of the encrypted files. Although this is still in the planning phases my plan is as follows From the perspective of a potential client of yours, I would want to encrypt my data locally and then deliver my encrypted data to your backup location without giving you the encryption key. I would want to transport it over an encrypted channel of course. And since it's encrypted data being transported then does it matter if someone sniffs it, even if they can somehow break the channel encryption?

I don't know that I would care if you added a layer of encryption on your end, as there's no way for you or anyone else to decrypt my raw data because I won't give you the key to begin with. We could just name my backup "jdjdicinfld137475" which gives no indication that it's mine.

---

### Post by kevdog on 2013-02-23
Ms Daisy

Yes you hit the nail on the head -- encrypt locally and send via encrypted channel to remote server.  I didn't know if encrypting the actual storage on the server was overkill  -- ie setting up an encryptfs folder in which the encrypted data gets stored.

Do you know of any better tools than possibly the ones I'm proposing?

---

### Post by Ms. Daisy on 2013-02-23
No, I don't aside from using ssh and each user keeps  their own private key.

I think the biggest concern in your setup is the access remote users have and/or can get. Ssh jail sounds good in theory, although I don't have any experience with it.

---

### Post by kevdog on 2013-02-24
I'll play around with some things and see what I can get going.

Thanks for your input.  Hopefully I can crack this nut!!

---

