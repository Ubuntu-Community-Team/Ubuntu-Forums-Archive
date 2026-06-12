---
title: "SSH - The Highs and Lows (HELP)"
date: 2005-10-19
forum: Server Platforms
---

### Post by TheGam on 2005-10-19
I decided yesterday to install SSH at home so could get access to my box from work etc.  I followed the starter guides and got working with passwords and then after a lot of mucking around got working with RSA Public key encryption.  I'd like to point out it wasn't not working cos of something odd was just I hadn't edited a line in the SSH-config file and it was trying to use DSA only.  The main thing is it made me look at all the options and play with keys and permissions more than I needed to, giving me a nice grounding in the commands and the way it works :) 

Well then I setup FireStarter, very nice I might add, with no problems.  Oh also have noticed a lot of people talking about wether they really need Public Key and maybe they should stay with passwords, I'm sure complex passwords are okish but I had a full blown dictionary attack on mh SSHD within 1Hr of it being running, checked it out and was some Korean University site :-)  Guessing some student wannabe hacker.

Anyway, back to the problem... Decided to reboot before I went to bed mainly to see if Firestarter and my LogChecker started automatically, but checked my new found baby SSH for good meassure, access denied!!!  So tryed evwerything and then eventually scrapped the keys and made new ones....  now it asks me for the passphrase but doesn't work and give me and odd msg 

debug1: PEM_read_PrivateKey failed

I have recreated the keys loads now, uninstalled SSH and reinstalled, checked and dbl checked both config files, checked the permissions etc.  Here is the full output:

OpenSSH_3.9p1 Debian-1ubuntu2.1, OpenSSL 0.9.7e 25 Oct 2004
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 127.0.0.1 [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/matt/.ssh/id_rsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.9p1 
Debian-1ubuntu2.1
debug1: match: OpenSSH_3.9p1 Debian-1ubuntu2.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '127.0.0.1' is known and matches the RSA host key.
debug1: Found key in /home/matt/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/matt/.ssh/id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/matt/.ssh/id_rsa':
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).


Any help would be really, really appreciated.

Thanks

Matt   :confused:

---

### Post by TheGam on 2005-10-19
Ok,  after a days rest solving Windows problems in my Job I came back with a fresh Linux solving mind.

I removed all the config files and then re-installed and went thru normal steps and worked first time, so I must have really mucked up my SSH-Config, cos my SSHD-Config was the same as the one I have now working.

Thanks All

:p

---

