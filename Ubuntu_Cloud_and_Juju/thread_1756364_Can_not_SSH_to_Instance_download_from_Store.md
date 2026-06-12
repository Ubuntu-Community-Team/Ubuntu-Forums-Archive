---
title: "Can not SSH to Instance download from Store"
date: 2011-05-12
forum: Ubuntu Cloud and Juju
---

### Post by lemon1707 on 2011-05-12
I had downloaded image on store and installed. But I can't ssh into instance when it's 

running. That is Ubuntu 9.10 - Karmic Koala (i386)

I try to delete all key : public and private keys.

Then, I create new key :

if [ ! -e ~/.euca/mykey.priv ]; then
    mkdir -p -m 700 ~/.euca
    touch ~/.euca/mykey.priv
    chmod 0600 ~/.euca/mykey.priv
    euca-add-keypair mykey > ~/.euca/mykey.priv
fi

Open ports :
euca-authorize default -P tcp -p 22 -s 0.0.0.0/0

Lauch instance :

euca-run-instances emi-DD74105B -k mykey -t m1.large

When the instance in running state, I ssh into it with user ubuntu first and then root user

ssh -i ~/.euca/mykey.priv ubuntu@$192.168.1.100 ( 192.168.1.100 , this is public ip of instance, I can ping it outsite)

But the error display :
Permission denied(Publickey).

I try to do many time, but It's still that error. 
Anyone got same error ? Is it the bug of Ubuntu ?

---

### Post by Rusty au Lait on 2011-05-12
Take the '$' out of the ssh command line. It is used to access the variable IPADDR only.

---

### Post by lemon1707 on 2011-05-12
> **Rusty au Lait said:**
> Take the '$' out of the ssh command line. It is used to access the variable IPADDR only.

sorry Rusty,
actually It doesn't have '$', It's attached when I was copying. 
I known that is purposes for security in Ubuntu system, but I had carry out in process.
Any other explain for this ? Please clarify that problem.

---

