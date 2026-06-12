---
title: "midnight commander and amazon s3"
date: 2016-09-02
forum: Ubuntu Cloud and Juju
---

### Post by maclenin on 2016-09-02
Just a quick wonder whether anyone knows whether it's possible to use midnight commander to access Amazon Web Services - specifically, their s3 storage service.

Am currently using the aws cli - which is perfectly fine - however, would be nice to be able to deploy mc (directly)!

Thanks for any guidance!

---

### Post by coldraven on 2016-09-03
I don't know if this would work and it is probably insecure.

> 


7.4 How do I do non-anonymous ftp with MC?[/h]  Non-anonymous ftp works just like the anonymous ftp but you give the login name with the host name.  For example, type "cd [&#8203;ftp://username@hostname]("ftp://username@hostname")". 



[http://www.midnight-commander.org/wiki/doc/faq](http://www.midnight-commander.org/wiki/doc/faq)

---

### Post by maclenin on 2016-09-04
Thanks for the reply, **coldraven!**

I think I have sussed a start (in xubuntu 16.04.1).

1. install midnight commander
```
sudo aptitude install mc
```
2. [install the aws cli using pip]("http://docs.aws.amazon.com/cli/latest/userguide/installing.html#install-with-pip")

3. [configure the aws cli]("http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html") to confirm your aws login credentials

4. confirm that your version of [boto is updated]("http://stackoverflow.com/questions/4940449/how-do-i-update-the-python-lib-boto") (see: [/usr/lib/mc/extfs.d/s3+]("https://github.com/MidnightCommander/mc/blob/master/src/vfs/extfs/helpers/s3%2B.in"))
```
pip install -U boto
```

5. set your [aws login credentials]("http://www.midnight-commander.org/ticket/3470") as [environmental variables]("https://help.ubuntu.com/community/EnvironmentVariables"), open midnight commander and cd to s3
```
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."
mc -b
cd  s3://
```

Good luck!

---

### Post by maclenin on 2016-09-06
A quick addendum:

I am encountering this bug / issue - with midnight commander - as I use s3 to host static web sites (so I have folder or bucket names example.com and a.b etc): [https://github.com/boto/boto/issues/2836](https://github.com/boto/boto/issues/2836)

I was able to access my s3 account using midnight commander before I created the example.com buckets.

The error appeared first as a I tried to create an example.com bucket using midnight commander.

I then created an example.com bucket via the web interface and now no longer have access to the buckets using midnight commander.

Access to s3 via aws cli and web are working fine.

The corrective suggestions contained in the link have not resolved the issue for me.

Thanks for any thoughts!

---

### Post by SeijiSensei on 2016-09-06
I use Linode for virtual servers so I don't know if this applies to AWS.  If it is possible to connect with SSH, then you can use [sshfs]("http://www.cyberciti.biz/faq/how-to-mount-remote-directory-filesystems-with-sshfs-on-linux/") to construct a full-time connection to the remote server.  This works best if you use "keys" to connect rather than entering a password.   Then the remote file system will be mounted into the local directory tree and should be browsable by any file manager including MC.

---

### Post by maclenin on 2016-09-08
Not clear whether this is the most prudent "solution" - however, it has resolved my boto issue, for the time being: [https://forums.aws.amazon.com/thread.jspa?messageID=470885#470885](https://forums.aws.amazon.com/thread.jspa?messageID=470885#470885)

I think I need to figure out how to resolve the ssl conflict - as already described in the [bug link]("https://github.com/boto/boto/issues/2836")...and as discussed, further, in a slightly different habitat, [here]("https://trac.cyberduck.io/ticket/3813")....

Not certain I need the permanent sshfs connection - though I will look into it and I'd like whatever I ultimately deploy to be secure....

MC is wonderfully quick to connect to aws - and simple and feature rich - like opening a terminal (or thunar) in a local directory....

Thanks for the advice!

---

