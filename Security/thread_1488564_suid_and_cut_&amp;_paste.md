---
title: "suid and cut &amp; paste"
date: 2010-05-20
forum: Security
---

### Post by tanoloco on 2010-05-20
Hi!

I created a testing folder with suid on it  e.g 
```
sudo mkdir test
sudo chow root:fuse test
sudo chmod 750 test
sudo chmod +g test
```now if I create a document in it, this would be root:fuse 750 and the same if I copy & paste any document into it, this would be changed into root:fuse 750

but if I cut & paste any document this will mantain its original ownership and permissions

I think this could be right if I paste it whatever but not into a folder with suid set where I suppose to inherit ownership and permissions of the suid folder.

Or am I  wrong?

Any chance to fix it obtaining what I want?

Thank you

---

### Post by teh_drizzle on 2010-05-20
So you're trying to set the setgid flag on the directory?

```
chmod g+s test
```

Now if you copy a file, into that directory (or create a new file there) it should inherit the group of the directory "fuse".

What problem are you experiencing?

---

### Post by tanoloco on 2010-05-21
Hello and thank you for your reply.
I will try to explain me better :)
Let's say  a sudoer creates a test folder somewhere like
```
sudo mkdir test
sudo chown bee:new test
sudo chmod 750 bee
sudo chmod +s bee
```I would like any document created inside the test folder to be bee:new

And this happens if:
1. a new document is **created** by bee
bee  is in a different default group let's say "def", so if he creates a new document inside the test folder this will be bee:new while anywhere else will be bee:def

2. a document with different ownership is **copied**.
let's say I have a document fou:fog somewhere if I copy it inside the test folder from bee its ownership will change into bee:new

But this doesn't happen if:
3. a document with different ownership is [B]cut and pasted
[/B]let's say I have a document fou:fog somewhere if I cut and paste it inside the  test folder from bee its ownership will remain fou:fog


I would like to know if there is a way to make cut & paste work  as copy, I mean to obtain the document's ownership to be changed form fou:fog into bee:new in the example, I mean automatically as copy does.

This because for example fou is not  a member of new, and bee is not a member of fog and so it's completely useless that the document keeps its original ownership because:
a. fou wouldn't be able to enter into the test folder which is beet:new 750 and do anything with that document
b. bee wouldn't be able to change the document which is fou:fog 750

and if bee isn't a sudoer he can't change the ownership of the document cut&pasted.

so the solution I found is that bee:
- cut&paste the document fou:fog into test folder
- copy it into the same folder: ownership will be changed from fou:fog  into bee:new but also the name will be changed from "xyz" to "xyz (copy)"
- delete the pasted document
- rename the copied document from "xyz (copy)" in "xyz"

but this annoying!

Is there a way that simply change the ownership from fou:fog into bee:new as cut&pasted?

---

