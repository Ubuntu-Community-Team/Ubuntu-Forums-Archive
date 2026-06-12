---
title: "Best practices for rsync as root with ssh keys?"
date: 2019-05-28
forum: Security
---

### Post by kpatz on 2019-05-28
I'm looking to tighten down some of the security on my Ubuntu systems especially in terms of automated processes that have to run as root... especially rsync based backups.

I've searched online, looked on ServerFault, StackOverflow, etc. and I get many solutions, but no one seems to agree on the best way to do it securely.

Currently, I have a file server with a zfs pool, and I pull backups from my other Ubuntu systems to this server using scripts that use rsync.  In order to back up everything and keep ownership/permissions intact, I run these as root.  I use sudo to run my backup script as root, and then the script uses ssh keys to connect to the other servers as root.  All the boxes have "PermitRootLogin without-password" in their sshd_config and all have the root account locked as is the Ubuntu way.

I also have a backup server with zfs where I send snapshots to from the main server using a script, and I also use ssh keys to send these as root.

These ssh keys don't have a passphrase since I need to have them run automated.  This of course is a (potential) security risk since if someone where to somehow gain access to the private key on my file server they could then gain a root shell on any of my boxes.  The file server is inside the LAN and not accessible from the internet in any way (unless someone gets through my firewall somehow, or cracks my 20+ character WiFi password).

Some articles recommend having rsync connect to the remote server as a non-root user and then use sudo from there, with NOPASSWD in the sudoers and using a command like "rsync ... --rsync-path="sudo rsync" ..." to gain root on the remote side.  Is this a better way than using a ssh key on root?  This would allow restricting the commands that can be run, and sudo keeps a better audit trail than sshd does.

I also found that there's a "forced-commands-only" option in PermitRootLogin in sshd_config.  Perhaps I should use that and restrict the key to running only the commands I need?

Thoughts?  I'm mainly looking for ways to make it "more" secure than it is now.... and learn more about security in the process.  Thanks!

---

### Post by TheFu on 2019-05-29
You are doing better than pretty much everyone outside professional setups already.
The only things I'd suggest looking into are

a) use a better backup tool that retains owner, group, permissions and ACLs over time, unlike rsync.  rsync has the last ownwer, group, and permissions if you are using the hard-link versioning technique. A good backup tool gets it all and for basically the same command, just swap out rsync for rdiff-backup. The command options are almost the same.

b) use a root-equiv "backup8532333" account (uid=0), not root and setup ssh keys for it.  Hackers will try root, but probably won't guess a funky account name.

c) limit the IP address(s) that backup8532333 can connect from to just the backup server. sshd_config has a Match.... capability.

d) use the ~/.ssh/config file to use different keys for pre-backup, backup, and post-backup commands on each of the remote systems.

e) I don't know if you use tcp-wrappers for fail2ban.  For systems that aren't internet facing, I setup tcp-wrappers to block all ssh access from outside the LAN.  For internet-facing systems where I need ssh access, I don't want to allow constant brute-force attacks even if I only allow ssh-key based authentication.

---

### Post by kpatz on 2019-05-30
> **TheFu said:**
> You are doing better than pretty much everyone outside professional setups already.
The only things I'd suggest looking into are

a) use a better backup tool that retains owner, group, permissions and ACLs over time, unlike rsync.  rsync has the last ownwer, group, and permissions if you are using the hard-link versioning technique. A good backup tool gets it all and for basically the same command, just swap out rsync for rdiff-backup. The command options are almost the same.I use rsync (or robocopy on Windoze systems) to backup non-ZFS partitions into zfs datasets that has daily snapshots, so that handles the versioning for me.  I'll have to research rdiff-backup though.> b) use a root-equiv "backup8532333" account (uid=0), not root and setup ssh keys for it.  Hackers will try root, but probably won't guess a funky account name.Good idea.  I may do that on the firewall box at least, though I have passwords disabled on ssh anyway so hackers can try all they want, they're not getting in. :)> c) limit the IP address(s) that backup8532333 can connect from to just the backup server. sshd_config has a Match.... capability.The backup server is on the LAN, so there's no internet access to either of these servers.  "Offsite" backups are on USB 3.0 drives I keep in my shed.  For home this is fine, but if I start doing this in a business environment I'll need something more robust.> d) use the ~/.ssh/config file to use different keys for pre-backup, backup, and post-backup commands on each of the remote systems.I'll have to look into this.  Do you think it's better for my main server to pull backups from the other boxes (as I do now) or have the other boxes push to the file server?  Pulling is simpler for me since i just go on the main server and run scripts to pull the backups (and then push a snapshot to the backup server afterward).  Plus I only have to keep root's private key on the one file server that's initiating the requests.> e) I don't know if you use tcp-wrappers for fail2ban.  For systems that aren't internet facing, I setup tcp-wrappers to block all ssh access from outside the LAN.  For internet-facing systems where I need ssh access, I don't want to allow constant brute-force attacks even if I only allow ssh-key based authentication.I have iptables rules to throttle ssh attempts from the internet.  I also run ssh on a non standard port on the firewall box, and password on root is disabled.  I almost never see an attempt since I picked a port that is almost never scanned by skiddies.  All these backup scripts are running on boxes inside the LAN.

I gather that ssh keys for root scripts is best, as opposed to sshing as a non root user and then running sudo?

---

### Post by TheFu on 2019-05-30
> **kpatz said:**
> I use rsync (or robocopy on Windoze systems) to backup non-ZFS partitions into zfs datasets that has daily snapshots, so that handles the versioning for me.  I'll have to research rdiff-backup though.Good idea.  I may do that on the firewall box at least, though I have passwords disabled on ssh anyway so hackers can try all they want, they're not getting in. :)The backup server is on the LAN, so there's no internet access to either of these servers.  "Offsite" backups are on USB 3.0 drives I keep in my shed.  For home this is fine, but if I start doing this in a business environment I'll need something more robust.I'll have to look into this.  Do you think it's better for my main server to pull backups from the other boxes (as I do now) or have the other boxes push to the file server?  Pulling is simpler for me since i just go on the main server and run scripts to pull the backups (and then push a snapshot to the backup server afterward).  Plus I only have to keep root's private key on the one file server that's initiating the requests.I have iptables rules to throttle ssh attempts from the internet.  I also run ssh on a non standard port on the firewall box, and password on root is disabled.  I almost never see an attempt since I picked a port that is almost never scanned by skiddies.  All these backup scripts are running on boxes inside the LAN.

I gather that ssh keys for root scripts is best, as opposed to sshing as a non root user and then running sudo?
[B]
Pull is always better than push.[/B] With push, the client, which may be 100% compromised will have access to keys on the system and will be able to corrupt all backups using the backup tools themselves.  With pull backups, the backup server, which we have to implicitly trust already, don't need to allow any access to the backup storage areas or allow the clients any access, direct or otherwise.

snapshots aren't a backup. They are useful for convenience, at least until the *zpull* command happens (I know zpull isn't a command).  Until the data gets off the client HDDs and placed in at least 2 other physical storage devices, then it isn't a backup. It is "hope." It is best if one of those devices is at least 500 miles away - to avoid region-wide disaster issues.  I love snapshots, but I use them as temporary tools that last no longer than a week, limited by available storage, of course.

Direct backup69348234 vs sudo?  I suppose if you lock down the sudo capabilities to only allow the 3 commands needed, that would be equiv, but once someone is into the machine, we have to assume it is compromised.  Which account would be more secure?  An account that is designed and only used for 1 purpose in life or another account?  For me, I'd probably a little lax about the sudo userid and might be tempted to use it for other stuff.  I know my backup6934823874 account cannot do anything else and it is a hassle to even access. Perhaps it is all in my head. IDK.

We never mentioned encryption of the backups.  That is also a best practice.  Think about the simple need to get warranty service on a HDD that won't spin up.  All our backup data is sitting there and we can't wipe it.  Do we eat the cost of the disk or ship it back, unencrypted, for an exchange/refurb?  I've eaten the cost a few times, before I started encrypting all data LVs.

Came across this [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid) - I know nothing about it, but seems like something a ZFS user could love.  Jim is a good resource about ZFS and storage and small-biz networking, if this is the same Jim from Ars.
[https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid)

---

### Post by kpatz on 2019-05-30
> **TheFu said:**
> [B]
Pull is always better than push.[/B] With push, the client, which may be 100% compromised will have access to keys on the system and will be able to corrupt all backups using the backup tools themselves.  With pull backups, the backup server, which we have to implicitly trust already, don't need to allow any access to the backup storage areas or allow the clients any access, direct or otherwise.Excellent points.  Especially pushing from Windows boxes.  Not sure how I'd do a pull backup from Windows to Linux though.  Right now I have a samba share to my "backup" ZFS dataset on the main server (ok, in the strict sense by your definition it isn't a backup, but it's the first stage of my overall backup scheme), and I robocopy anything I want copied from Windows to this share.  For Linux I use rsync, so nothing is accessible except via rsync.> snapshots aren't a backup. They are useful for convenience, at least until the *zpull* command happens (I know zpull isn't a command).  Until the data gets off the client HDDs and placed in at least 2 other physical storage devices, then it isn't a backup. It is "hope." It is best if one of those devices is at least 500 miles away - to avoid region-wide disaster issues.  I love snapshots, but I use them as temporary tools that last no longer than a week, limited by available storage, of course.The snapshots are just the first stage of my overall scheme... these then get pushed to the backup server's zfs pool, and I also send them weekly to 2 separate, encrypted external USB drives which I store in my shed when they aren't being backed-up to.  Ok, they're not 500 miles away, but if there's a region wide disaster, I'll have bigger things to worry about than my data anyway.  I don't trust the cloud, and backing up 2+ TB there is not practical anyway, but I could take my most critical files, encrypted, and back it up there for that sort of situation.

Sure, daily backups are better than weekly, but I don't produce or change a lot of data over the course of a week, so it's not a big tragedy if I lose a few days' worth.  If I have something really important I'll back it up to somewhere as soon as I create it.

But then, this thread is more about the best way to access root across boxes securely for the purposes of doing backups, as opposed to how good, or bad, my backup scheme is. ;)  Everyone's backup needs are different.

I'll have to do the "uid 0 but not root" account thing, and limit the key(s) to running just the commands needed by my scripts.  I'm also going to replace all my older RSA keys with ed25519 keys.  I guess my goal is to ensure, that if someone, somehow were to get access to one of my boxes, that they couldn't easily gain root on that box or on any other boxes.  I suppose at that point, once they're in they're in, but slowing them down some is never a bad thing.

One thing I do is I give each client machine its own key, and any boxes I need to ssh from that client gets that key added to .ssh/authorized_keys.  That way, if a client machine grows legs and walks off, or I replace it, I can simply remove that key from authorized_keys and that client can no longer access my systems, but other clients still can with their keys.

> We never mentioned encryption of the backups.  That is also a best practice.  Think about the simple need to get warranty service on a HDD that won't spin up.  All our backup data is sitting there and we can't wipe it.  Do we eat the cost of the disk or ship it back, unencrypted, for an exchange/refurb?  I've eaten the cost a few times, before I started encrypting all data LVs.My ZFS pools aren't currently on encrypted drives since ZoL doesn't (yet) support native encryption, and running ZFS on an encrypted container like luks is generally not considered advisable for stability.  I do have some encrypted zvols for sensitive data.  My 2 external drives are LUKS encrypted, that way if they grow legs and walk away they won't be accessible.  Perhaps next time I build a new server I can enable hardware encryption on the drives in my zpool.> Came across this [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid) - I know nothing about it, but seems like something a ZFS user could love.  Jim is a good resource about ZFS and storage and small-biz networking, if this is the same Jim from Ars.
[https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid)Cool stuff, I'll have to check it out.  Might be overkill for my home network use case, but it might be educational.

Thanks. :)

---

### Post by SeijiSensei on 2019-05-30
I back up my remote servers with rsync over the OpenVPN tunnels that link them to my home office.  All access to my servers goes over the VPNs except for the the usual public-facing services like HTTP and SMTP.

---

### Post by kpatz on 2019-05-30
I've been changing all my ssh keys over to ed25519 and have them all working.  I also restricted the key in the /root/.ssh/authorized_keys of each box having backups pulled to only be accepted from the IP address of my main file server:  **from="192.168.x.x" ssh-ed25519 key-stuff-goes-here...**

So, in order for a hacker to gain root using this key, they'd have to get past my firewall (or be physically close enough to connect to my wifi AND crack its password), get into my main file server, gain root there, then get the key and ssh to the other boxes FROM there.  Pretty darned unlikely... I'm guessing "secure enough" for my needs.

I also found my authorized_keys files and known_hosts files on each box were cluttered with keys from old, outdated systems (in some cases)... I've cleaned them out and now only boxes that need a key to access another box have a key in place and access granted to that key on the target box.  If I ssh in from my laptop, even from remote, I use an agent so my laptop's key will let me box hop if needed.

Firewall's ssh is locked down tightly as well especially on the WAN side.  It's on an obscure port, iptables throttled, no password authentication, no root logins... good luck gettin' in the usual ways anyway!

---

### Post by TheFu on 2019-05-30
Nicely done.

Over the years, ssh and wifi **have** had security issues, so having multiple layers is always good.

I started moving my keys to ed25519 a few months ago after the last 14.04 box was retired. Still have 1 network device that doesn't support them. Booo.

And nobody should believe that my setup is perfect either.  There is always the "desired state" that I'm working towards, but life does get in the way sometimes. The "desired state" is a moving target, constantly.

---

### Post by kpatz on 2019-05-30
Yep... I just retired my old 14.04 firewall box... replaced it with 18.04... redid my scripts to work with networkd and systemd... have it working pretty well, though I'm still "fixing glitches." LOL.  While reading up on new 18.04 features, that's when I discovered the newfangled ed25519 keys being "better" than the RSA keys I'd been using.  At least 16.04 supports these so I'm good... my other 'buntu boxes are on 16.04.

I'm open to any other security tips... I'm trying to learn and master the fine art... even if I don't need any more on my home network, knowing how can be useful.  And I'll admit my setup isn't perfect either (well, who's is? LOL).  It's better than it used to be, that's for sure, especially in terms of backups.  ZFS made life a lot easier in that regard.

Another thing I do now, which is sort of another form of "backup", is when I buy a new piece of hardware to install a new server on (such as my firewall), I keep the old one as a spare.  That way, if the new one poops the bed, I can just swap in the previous one and be back up and running in a jiffy.  At some point I'll upgrade the old one to 18.04 so it's current, and when 20.04 comes out and becomes stable, I can install that on the old box and then swap it in once it's ready.  Having extra hardware for these upgrades is handy since I basically have no downtime due to upgrades.  Of course, anything that can be done in a VM can do this without additional hardware, but not everything is suited for a VM... like the VM host itself... or a firewall.

When I decommissioned my (ancient) file server running 10.04 a few years ago, I built a new box with 16.04 which is my main file server, and then I also installed 16.04 on the old box and made that my backup server.  So this is a good way to gain backup hardware without having to invest in more hardware... well, more than needed.  I did replace the drives in the old box.

---

