---
title: "Samba shares inaccessable"
date: 2012-06-30
forum: Server Platforms
---

### Post by thehiers on 2012-06-30
I'm fairly new to ubuntu and have been asked to figure out why the samba shares on a ubuntu 10.x server have become inaccessible.  Here are the details:

Office staff suddenly cannot access their samba shares from their mac osx clients.  They can connect to the server, it accepts password, shows the available shares, but when one is selected (any of them except netlogon), user gets the message "Connection failed.  There was an error connecting to the server "192.168.10.11"  Check the server name or IP address, and then try again."

The samba log file only says:

[2012/06/29 07:12:15,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service shared, path /home/shared

However, root CAN connect to any of the shares successfully from the same client machines.

Smb.conf has not changed since the problem started, and the folder permissions look correct.

Samba has been restarted.

The samba documentation I find online shows access can be given to clients in the smb.conf file using "valid users" variable, but this is not how this particular implementation has been configured.  

Where else should I look to find the source of the problem.  Are there other methods to give access to samba shares than using the smb.conf options?

Thanks
Richard

---

### Post by rmaultz on 2012-06-30
You can  find samba documetation going to  [www.samba.org](www.samba.org)   or  from terminal  type  man samba

There is a wealth of information  by just googling too  and  youtube   i found these  sources helpfull

---

### Post by srivo on 2012-07-01
Can you post the smb.conf file?

---

### Post by luvshines on 2012-07-01
> **thehiers said:**
> The samba log file only says:

[2012/06/29 07:12:15,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service shared, path /home/shared

However, root CAN connect to any of the shares successfully from the same client machines.

I wild guess here, but maybe it looks like the shared path doesn't have permission for user read and execute.

Please check that the complete path starting from root[/] right upto the shared directory has read(r) and execute(x) permission for the user who is trying to connect. If all the shared paths lie under same directory then I think the take care of the others permission (d------r-x)

---

### Post by thehiers on 2012-07-02
> **luvshines said:**
> I wild guess here, but maybe it looks like the shared path doesn't have permission for user read and execute.

Please check that the complete path starting from root[/] right upto the shared directory has read(r) and execute(x) permission for the user who is trying to connect. If all the shared paths lie under same directory then I think the take care of the others permission (d------r-x)

Thanks.  That did it!  Why would the permissions for the /home and /home/shared folders have changed?

---

