---
title: "Automate add user"
date: 2013-07-15
forum: Server Platforms
---

### Post by cludgie on 2013-07-15
Hello all,

I have a list of dozens of new users that I'd like to create on my Ubuntu Server running 10.04. I'm still a novice and was hoping someone could point me in the right direction for automating the process. I

I was thinking along the lines of saving a list of users/usernames then doing the following:

```

cat list | while read name
do
adduser $name.....

```

 Or could I use expect?

Thanks
Cludgie

---

### Post by Cheesehead on 2013-07-15
Running adduser non-interactively: See a (somewhat terse) solution at [http://askubuntu.com/questions/94060/run-adduser-non-interactively](http://askubuntu.com/questions/94060/run-adduser-non-interactively)

---

### Post by sisco311 on 2013-07-15
You can use the newusers command. Check out its man page for details.

If you have any further questions, please feel free to ask.

---

