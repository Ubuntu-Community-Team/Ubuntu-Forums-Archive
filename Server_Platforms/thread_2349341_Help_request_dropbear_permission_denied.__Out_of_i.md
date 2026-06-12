---
title: "Help request: dropbear permission denied.  Out of ideas!"
date: 2017-01-13
forum: Server Platforms
---

### Post by SparkyUSN on 2017-01-13
Edit: one place to start may be to get me into the busy box shell so I can see what dropbear is doing or failing to do.  I'm having trouble getting initramfs to build with the correct options.  Thoughts?  

Running 16.04.1 LTS with an encrypted root volume.  I've installed dropbear, which runs when the initramfs starts to allow the root volume to be unlocked.  OpenSSH runs when the full server is up and running.  When I try to ssh -v into the dropbear instance (before the root volume is unlocked, that is), I get 

```
OpenSSH_7.3p1, LibreSSL 2.4.1
debug1: Reading configuration data /Users/mws/.ssh/config
debug1: /Users/mws/.ssh/config line 6: Applying options for foundation
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 20: Applying options for *
debug1: Connecting to 192.168.1.6 [192.168.1.6] port 22.
debug1: Connection established.
debug1: identity file /Users/mws/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/mws/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.3
debug1: Remote protocol version 2.0, remote software version dropbear_2016.72
debug1: no match: dropbear_2016.72
debug1: Authenticating to 192.168.1.6:22 as 'root'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp521
debug1: kex: server->client cipher: aes128-ctr MAC: hmac-sha2-256 compression: none
debug1: kex: client->server cipher: aes128-ctr MAC: hmac-sha2-256 compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp521 SHA256:H0OxOCKeD1aRYgpvbtaH8XsDiM/dr4aSffVPgU7EAoc
debug1: Host '192.168.1.6' is known and matches the ECDSA host key.
debug1: Found key in /Users/mws/.ssh/foundation_known_hosts:1
debug1: rekey after 4294967296 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: rekey after 4294967296 blocks
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/mws/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /Users/mws/.ssh/id_dsa
debug1: Trying private key: /Users/mws/.ssh/id_ecdsa
debug1: Trying private key: /Users/mws/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).
```

I can ssh into the OpenSSH server once I unlock it locally, and I've verified that the public keys used by dropbear and OpenSSH are the same.  The dropbear authorized login keys are located at /etc/initramfs-tools/root/.ssh/authorized_keys and they match the keys at /home/me/.ssh/authorized_keys.  I've even verified that I'm putting the dropbear authorized key file in the correct place with the /usr/share/initramfs-tools/hooks/dropbear file, which copies the authorized_keys file from the location I just mentioned.  

Clearly the local machine finds the key I want to use (and the correct key that works when OpenSSH is running) and offers it.  Dropbear just rejects it.  

Anybody have any idea why dropbear won't let me login?   Or at least how to get my dropbear server to show me its equivalent of /log/var/auth.log?  That would at least show me the flavor of the issue if not the solution.  I realize that it could be a user issue on the initramfs, but I don't know how to verify that.  I've looked at the /usr/share/initramfs-tools/hooks/dropbear file and it creates a /etc/passwd file that says ```
root:*:0:0::${home#$DESTDIR}:/bin/sh
``` and an /etc/group file that says ```
root:!:0:" >"$DESTDIR/etc/group
```, where $DESTDIR is root-[random six-character suffix].  I've even tried adding a line in that file that inserts a different user into passed and group with "x" in the password field and attempting to login as that user.  All to no avail.

I've checked the permissions on dropbear's authorized_keys file by adding the line ```
ls -la "$home/.ssh/authorized_keys"
``` to the ...hooks/dropbear file.  When I update-initramfs it then shows me that the .ssh directory is drw-------- and the authorized_keys file is -rw-------.  Furthermore, I believe the ...hooks/dropbear script is built to throw an error if the authorized_keys file is not acceptable when update-initramfs is run.  There are no update-initramfs errors.

Could it have something to do with the ssh debug line that says ```
no match: dropbear_2016.72
```?  I don't know what file it is matching the remote protocol against.

Sincerely appreciate any thoughts or pointers the group has for me.  I've been beating my head against this for hours, periodically running upstairs to locally unlock my server hard drive to try something new.  I'm admitting defeat and asking or help.

---

### Post by SparkyUSN on 2017-01-14
Answering my own request because I figured it out, at least partly, and I'll leave it for Internet in case somebody else can use it.

The dropbear hook in the initramfs build process puts the authorized_keys file in a folder named root-DHSkw (root- plus a five-letter suffix that changes each time update-initramfs is run).  That same hook file then adds the user root to the passed and group file (to facilitate login once dropbear is running).  With this setup, if you login as root, dropbear finds no authorized_keys in the /root/.ssh/ directory.  If you login as root-xxxxx, that user (root-xxxxx) has no entry in /etc/passwd/.  Only root has an entry in /etc/passwd.

If history is a guide, I've missed something and the smart folks that created dropbear built it correctly and I'm just using it incorrectly.  I'm working to figure that out right now.  I used the break=mount boot option to drop into the initramfs busybox shell, at which point I was able to copy the authorized_keys file from /root-xxxxx/.ssh to /root/.ssh. After that copy action I was able to successfully login with an SSH private key that corresponds to one of the public keys in /root/.ssh/authorized_keys.

Hallelujia. Thanks for all that looked at this for me.

---

### Post by SparkyUSN on 2017-01-15
Canonical bug report [here]("https://bugs.launchpad.net/ubuntu/+source/dropbear/+bug/1645555").

---

