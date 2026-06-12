---
title: "VSFTPD, SFTP, and Authorized Keys"
date: 2012-01-22
forum: Server Platforms
---

### Post by hibliss on 2012-01-22
So I have two servers, one at home running 10.04 LTS and one remote also running 10.04 LTS.

In an effort to improve my security, I recently disabled password authentication and enabled the option in sshd_config to only allow login with ssh keys. Everything is fine here and I feel more secure already.

Now for the issue. I use command line sftp to transfer files between the two servers with no GUI in GNU Screen. This allows the transfer to run in the background.

After disabling password authentication, I can no longer login and transfer files with this command:

```
sftp -o Port=2244 user@myserveraddress.com
```

I now get the following output:

```

Permission denied (publickey).
Couldn't read packet: Connection reset by peer

```

So I did some research and it seems I have some options to do password free authentication using SSL using FTPS instead of SFTP. 

Is there an easier way to accomplish my file transfer? Maybe rSyncing a folder where I copy the files I want? Any recommendations? 

Thanks

---

