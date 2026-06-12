---
title: "Cloud - Images instance automatically terminating?"
date: 2011-10-02
forum: Ubuntu Cloud and Juju
---

### Post by thrainpa on 2011-10-02
After I installed a cloud controller and node on separate machines, they automatically registered each other correctly.

Unfortunately (as it seems to be a common issue with server 11.04), the image store doesn't work due to a certificate failure.
So I installed an image manually then ran it with code:
```

wget http://eucalyptussoftware.com/downloads/eucalyptus-images/euca-ubuntu-9.04-i386.tar.gz

uec-publish-tarball euca-ubuntu-9.04-i386.tar.gz

EMI=$(euca-describe-images | grep emi- | head -n1 | awk '{print $2}')

euca-run-instances $EMI -k mykey -t c1.xlarge

```

After this the instance should be created and run, however when I run:
```

watch -n5 euca-describe-instances

```

and keep an eye on the progress I see that after it has finished 'pending', the instance status goes instantly into 'terminated' status.

Can anyone help me figure out why and how to fix this?

[SOLVED]

My apologies, but I found out the problem, I don't think the tutorial instructs me to cd to the ~/.euca folder, but doing this has fixed the issue, I hope this helps someone.

---

