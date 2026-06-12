---
title: "encrypted remote backups over ssh?? how?"
date: 2009-07-22
forum: Security
---

### Post by jimmybarcelona on 2009-07-22
My basic need is to archive and encrypt files and store them on a remote server on my local network. Currently I can use tar and pipe the output over ssh to the remote server, but then I have to encrypt it on the other end. I can use tar and pipe the output to gpg and get an encrypted archive, but then I have to move it. is there a way to do all of this in one step? i.e.... tar file | gpg encrypt | transfer via ssh  ?

that way I can have it done automatically.

---

### Post by Dave_Connor on 2009-07-22
```
tar file && gpg file && ssh file server 
```

That will issue the tar command and then gpg command and then send over the encrypted file to your server.

---

### Post by Agent ME on 2009-07-23
Tar'ing to a file, then encrypting is redundant and slower than simply piping tar's output to gpg:
```
tar -cvz somefolder/ | gpg -er recipient@emailaddress.com -o file.tgz.gpg
```
That directly tars and encrypts something. You could then scp that file over.

Or instead, if you think a bit more creatively, you can pipe everything directly:
```
tar -cvz somefolder/ | gpg -er recipient@emailaddress.com | ssh remote-host "cat > file.tgz.gpg"
```
With the above solution, no temporary file even needs to be made on the current computer to be sent. It's all piped over as it's generated.

---

### Post by jimmybarcelona on 2009-07-23
Thanks so much guys, worked like a charm. I had to generate and export a set of keys though. Conventional encryption doesn't seem to work well when piped through ssh, don't know why.

---

### Post by dragos2 on 2009-07-23
> **jimmybarcelona said:**
> Thanks so much guys, worked like a charm. I had to generate and export a set of keys though. Conventional encryption doesn't seem to work well when piped through ssh, don't know why.

Or you can compress it hard before sending down the wire like this:

```

tar -cvz folder |   7z a -si -t7z -m0=lzma -mx=9 -md=128m file.gz.7z | ssh remotehost file.7z

```Ps: I am not sure this will send it directly ranther than first store then send.

---

### Post by Agent ME on 2009-07-24
> **jimmybarcelona said:**
> Conventional encryption doesn't seem to work well when piped through ssh, don't know why.
What do you mean by that? The example I posted works fine.

> **dragos2 said:**
> Or you can compress it hard before sending down the wire like this:
```
tar -cvz folder |   7z a -si -t7z -m0=lzma -mx=9 -md=128m file.gz.7z | ssh remotehost file.7z

```Ps: I am not sure this will send it directly ranther than first store then send.
Your command compresses it twice (which does nothing other than take time and make it more complex to open later), doesn't encrypt it at all, and fails to send it correctly.

---

### Post by mogliii on 2009-09-21
Hi,

I am playing around with this encrypted backup over pipe. However I have a problem with tar -> openssl -> ssh:


The command I am using is:
```
tar czvpf - /home/user | openssl aes-256-cbc -salt | ssh user@server "cat > /home/user/backup.tar.gz.aes-256-cbc"
```

resulting in the following output:
```
file1
file2
...
(maybe 30 files)
...
user@server's password: 
Verifying - enter aes-256-cbc encryption password:
verify failure
bad password read

```

I typed in the ssh password, but then openssl thinks that the ssh password is also for itself. This means the first password entry is grabbed by both, ssh and openssl. 

If I specify the -k password option for openssl, there is no problem.

Is this a bug? In bash, ssh or openssl?

---

### Post by jimmybarcelona on 2009-09-21
I don't know why that is, I only know what I did to get around it. I just switched to public key with gnupg instead. That took out the need for a password altogether, enabling me to completely automate the backups using shell scripts. (Sorry I couldn't answer your question better. I'm still fairly new at this myself).

---

### Post by bodhi.zazen on 2009-09-21
You can mount a remote directory with sshfs

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

