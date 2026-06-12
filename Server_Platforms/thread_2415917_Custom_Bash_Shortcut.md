---
title: "Custom Bash Shortcut"
date: 2019-04-02
forum: Server Platforms
---

### Post by zoobuntufan on 2019-04-02
[FONT=&quot]I frequently have to scp files from my Ubuntu Server 18.04 over ssh to a client.  Is there a way to make a key binding/shortcut to the client address to prevent typing out the full 'ssh leon@192.168.50.178' every time? It would be something like scp file.txt Ctrl-i in place of the client path. I've looked into bind and alias with no success. Any help appreciated. Thanks![/FONT]

---

### Post by sisco311 on 2019-04-02
How about  a function?

[http://mywiki.wooledge.org/BashGuide/CompoundCommands?highlight=%28function%29#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands?highlight=%28function%29#Functions)

```
cptoleon()
{
    scp "$@" target
}
```

---

### Post by TheFu on 2019-04-02
Or just setup a stanza in your ~/.ssh/config file ... 
```
host anything-you-like
        user leon
        hostname 192.168.50.178
        port 22

host crm-do
    user az8843423432
    hostname some.digital.ocean.place.com
    port 60022

```

So from now on, any ssh-based access to "anything-you-like" will automatically fill in the userid@IP with the port you want.  Have more places to contact?  Just add another stanza.  Only the host part is required.  hostname can be an IP or DNS name.

The manpage for ssh_config spells out all the options.  There are lots of other options, tunnels, keepalive settings, different keys, it really is great.

The commands which honor this config are all the ssh-based ones - so ssh, scp, sftp, rsync, sshfs, rdiff-backup, vim rsync://, any of the file managers that use ssh:// or sftp:// URLs.  x2go and other NX based remote desktops also honor this config file.  I can't think of any ssh-based connect that doesn't honor it.

And obviously, if you setup ssh-keys and use ssh-copy-id to push the public key to the other system, then the connection authentication will be much more secure and much more convenient.  Just not having to deal with the odd port options for rsync vs ssh vs scp vs rdiff-backup makes this worth while.

---

### Post by zoobuntufan on 2019-04-02
I’ll look into this. I should have mentioned that I am using SSH to log into the server from the client I am copying to in the first place.

---

### Post by TheFu on 2019-04-03
> **zoobuntufan said:**
> I’ll look into this. I should have mentioned that I am using SSH to log into the server from the client I am copying to in the first place.

You do realize that you can directly "pull" the files via scp, correct?

```
$ scp anything-you-like:/path/to/file.txt .
```

Or if you prefer

```
$ scp leon@x.x.x.x:/path/to/file.txt .
```

Or put the file somewhere other than PWD
```
$ scp leon@x.x.x.x:/path/to/file.txt ~/Downloads/
```

rsync works as easily and is commonly used in automation.  rsync uses ssh for network transfers, hence, ssh authentication and ssh-keys work too.  If you know the file(s) get updated daily, I'd automate having them copied.  Actually, I do this with my password manager DB file.  Every night, just after midnight, it gets copied to 4 other computers/devices, automatically.

---

### Post by zoobuntufan on 2019-04-03
I did not know that! I’m using SSH keys so I will try this out. Thanks!

---

