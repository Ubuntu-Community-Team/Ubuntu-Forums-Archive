---
title: "How-to setup per-user sshd port forwarding ?"
date: 2007-11-20
forum: Server Platforms
---

### Post by delerious010 on 2007-11-20
I've got a linux Router that permits SSH port forwarding so that I can tunnel into my network from remote locations ( either to a Xen Server or other machines ). And I'd eventually like to allow other users to tunnel into specific Hosts/Ports ( various Xen servers / services ) while maintaining full access myself.

The problem with this, however, is that the users would be able to forward any port to any host and I'd very much want to prevent that.

Is there a way to limit individual's port forwarding rules ?
Specifically, a per-user/per-group iptables hook or anything of the sort would be good .. 

Any help, pointers, links, etc.. would be appreciated !

---

### Post by colo on 2007-11-20
Iirc, you should be able to do that with the grsec-patchset of the Linux kernel. It might also be possible for Apparmor, though I have to admit I've never looked into its feature-list or mission statement.

---

### Post by delerious010 on 2007-11-20
Good ideas, I'll keep that in mind .. I'll hold off for now though as that seems a bit much... 

I've searched a bit, and the following seem promising, and worth a try as well : 

- iptables with --uid-owner / --gid-owner matches ( not sure if these apply with ssh forwarding/tunneling )
- a custom SSHRC script which matches via $( groups )
- tcp wrappers to ALLOW / DENY connections
:: draw back is this is system-wide as opposed to user-specific since it's <service>:<host>
- public key based configurations that limit what is allowed
:: might work for a limited amount of users ,, seems like a maintenance nightmare in the long run.

---

### Post by delerious010 on 2007-11-21
In the end, I've opted for Pub key authentication.
If it helps anyone, here's what I did...
If yall haver a Better Way (tm), feel free to post.

To configure : 
1) Create keys : ssh-keygen -t rsa
2) Make sure they are stored in proper place for ssh to read them
    ( ex.: On my wrt, /etc/ssh/authorized_keys )
    :: Security concern : If the keys are in /etc/ssh/authorized_keys as opposed to ~/.ssh/authorized_keys, 
        that file must be readable by everyone that connects ( chmod, and possibly chgrp ). Having the keys in the user's homes is potentially safer.
3) cat <key>.pub >> /etc/ssh/authorized_keys
    chmod 0600 /etc/ssh/authorized_keys
4) modify key line in /etc/ssh/authorized_keys with : 
no-port-forwarding,no-agent-forwarding,permitopen="<dest host of forward>:<dest port of forward>",permitopen="...another one..." ssh-dss <the key> <the comment>
5) If you want the key to be used only for forwarding, while denying the ssh console, add command="/bin/false" to the beginning of the line in 4). This command will be executed first thing as soon as the session is established.

To test : 
1) Copy the key ( not the .pub ) to the client home's ~/.ssh/
2) Establish a connection : 
ssh -v -L <locally forwarded port>:<destination host>:<destination port> <username on forwarding host .. router>:<forwarding host .. router>
Note : If using command="/bin/false" as detailed above, you need to add a -N switch to the ssh command, else the ssh session will terminate.
Note : Through me off at first that you DO get a bash prompt on destination machine. With "-v" you'll see that forwarding is disabled.

3) Test the connection : ( in another terminal ) : 
ssh -p <locally forwarded port> localhost

Note : Attempting to connect to anything NOT in permitopen returns : ssh_exchange_identification: Connection closed by remote host

---

