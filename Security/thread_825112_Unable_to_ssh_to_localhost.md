---
title: "Unable to ssh to localhost"
date: 2008-06-10
forum: Security
---

### Post by amishphysicist on 2008-06-10
Heya,

I've been trying to get ssh working on my machine and have had no luck.  I was directed from my [original thread]("http://ubuntuforums.org/showthread.php?p=5158461") over here, since it appears to be more than the usual sshd problems.

I've attached my sshd config (as well as my ssh config) as they asked in my previous thread.

Please refer to the other thread for more info about the actual commamds I used to get things installed.

thanks,

-nate

---

### Post by HalPomeranz on 2008-06-10
In your other thread, you showed this output from your "ssh localhost" command:

```

nlieby@nlieby-lin:/lsurf/var$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 3b:9b:c7:f4:ee:18:67:3f:4c:ad:86:48:5f:7a:14:81.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.

```

There must be more to this output.  Do you get a password prompt after this?  The output above makes it look to me like things are working-- you can ssh to localhost and talk to the SSH server.  So I'm not seeing where your problem is.

---

### Post by amishphysicist on 2008-06-10
Yeah. There's a password prompt, but it doesn't accept my password (tried umpteen times, capslock isn't on, etc).

Additionally, I re-tried sshing into my machine from a remote machine using the IP, rather than the hostname and got the same results.  Password prompt, but no acceptance.

So I guess this is two issues now:

1) Why isn't my hostname resolving (since I can hit it by using IPs)
2) Why can't I login using my normal password?

Do I need to do some crazy user creation or add my users to some ssh-ers group?

thanks,

-nate

---

### Post by HalPomeranz on 2008-06-10
> **amishphysicist said:**
> 
1) Why isn't my hostname resolving (since I can hit it by using IPs)
2) Why can't I login using my normal password?


1) Because you haven't registered a record for your host into your local DNS server?  Other machines don't automatically learn your machine's host name just because you plug the machine into the network.  There's some administrative magic that needs to happen here.

2) This one's more interesting.  Let's verify that you're correctly typing your password.  Run this command:

```

sudo wc -l /etc/shadow

```

You should be prompted for your password-- let me know if the password you've been typing works in this case.  If it does, then it's definitely something hinky with SSH.

---

### Post by amishphysicist on 2008-06-10
Bring on the hink... It's taking my password fine.

---

### Post by HalPomeranz on 2008-06-10
> **amishphysicist said:**
> Bring on the hink... It's taking my password fine.

OK, I think I see your problem.  This line in sshd_config is messing you up:

```

AllowUsers $USER_1 $USER_2 ... $USER_N

```

If AllowUsers is set, then only the listed users are allowed to log in.  However, the values on the line above are not valid users.  If you wanted to only allow your username to log in, you would write:

```

AllowUsers nlieby

```

You could also completely remove the AllowUsers line and then any valid user in your password file would be allowed to log in.

---

### Post by amishphysicist on 2008-06-10
Yes!  That fixed it. Thanks a ton.

---

