---
title: "Overthewire - bandit 16 --&gt; 1"
date: 2018-11-21
forum: Security
---

### Post by nissen on 2018-11-21
Hi people, 

I'm struggling with bandit level 16. I've read from [https://www.yalpski.net/bandit-wargame/bandit-walkthrough-level-16](https://www.yalpski.net/bandit-wargame/bandit-walkthrough-level-16) that I've to do three steps: 
1. search for open ports in range 31000-32000 (done)
- I found two port: 31518 and 31790

2. search which ports speak SSL (done)
- 31518 speaks SSL, 31790 doesn't

3. create own private key to connect to next level (here I'm stuck) 

I have searched on Google for generating a SSH key, and I've used following command: ```
ssh-keygen
``` but I following error  ```
Saving key "/home/bandit16/.ssh/id_rsa" failed: No such file or directory"

```

I don't know to generate the key and how to use it for connecting to next level.

Does someone know how to proceed and can give me some hints? :)

I now figured out how to create the ssh-key.

I had to create a directory using following command: ```
mkdir /tmp/kenken/
``` where I created the ssh-key and renamed the ssh-key.

But I'm not sure this is the right way to go and I don't can figure out how to use the ssh-key to proceed :)

I figured it out. I had to run this command: 

```
echo cluFn7wTiGryunymYOu4RcffSxQluehd | openssl s_client -quiet -connect localhost:31790 
```

Then a RSA private key was printed to stdout. This private RSA key should I copy/paste to a txt.file. Then I should change right, using chmod 600 file.path

Then I could run ```
ssh -i file.path bandit17@localhost 
```and I was at level 17. 

I have a question. When I ran this command:

```
echo cluFn7wTiGryunymYOu4RcffSxQluehd | openssl s_client -quiet -connect localhost:31790 
```

a private RSA key was printed to stdout. Why is that key being printed to stdout and what is it?

---

### Post by QIII on 2018-11-21
Hello!

Please use the default font and color unless there is a compelling reason to draw attention to a particular part of your post.

Also, please enclose all terminal commands and their output in code tags.  This makes your posts easier to read and preserves formatting.

To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and click the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by nissen on 2018-11-23
> **QIII said:**
> Hello!

Please use the default font and color unless there is a compelling reason to draw attention to a particular part of your post.

Also, please enclose all terminal commands and their output in code tags.  This makes your posts easier to read and preserves formatting.

To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and click the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

I'll will remember it in the future - thank you :)

---

