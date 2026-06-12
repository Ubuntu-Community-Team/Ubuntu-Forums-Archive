---
title: "Storing Environment Variables Permanently"
date: 2012-05-21
forum: Ubuntu Dev Link Forum
---

### Post by cheerPuncH on 2012-05-21
Hi,

I'm a bio-info programmer and I'm writing a script that uses perl modules in ubuntu. It "Can't locate AMOS/AmosLib.pm". So I do the following.
> find ./ -name "AmosLib.*"	
> export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib:$PERL5LIB

This works fine! The error is eliminated. It can find the module. Oops, but when I exit the terminal and open a new one I have to set the environment variable all over again. Is there a way for me to set this permanently? And in which sh would be most appropriate? /etc/profile, bashrc? Do I just copy and paste the export line into one of the shell files? Is it as easy as that? Or do I have this all wrong? (I have root access)

Thanks for all your help in advance!

Jeri

---

### Post by papibe on 2012-05-21
Hi cheerPuncH.

Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1984328") and [this]("http://ubuntuforums.org/showthread.php?t=1974991&highlight=environment+bashrc").

Regards.

---

### Post by cheerPuncH on 2012-05-24
Hi papibe!

Thanks for your response. Here's what I've done.
$ gedit ~/.bashrc
Within gedit, at the very bottom, I put...
export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib

I tried it with and without a semi-colon at the end followed by a restart. Both times I tried running my program and it complained the same.

Maybe I'm having a different issue? 

I also have export PERL5LIB="/home/diltsjr/perl5/lib/perl.... in the .bashrc. Should I have just added the path to that variable? It has quotes around it and a semi-colon at the end. I don't know if I'm even putting the export in the right place.

So, this time I tried running the export in the terminal and checked to see if the program worked (in the same terminal), like I said it did in my previous post and it didn't! I didn't move any directories or files so now I'm in a tizzy.

Could you guide me, if you can?

Thanks,
Jeri

---

### Post by papibe on 2012-05-24
I believe what you are trying to do is add the AMOS library to the variable, right?

This:
```
export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib
```
would replace its previous value with just the amos library path.

Instead, add the same line that was helping you on your interactive session:
```
export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib:$PERL5LIB
```
That way your are keeping its old value and pasting the amos library.

To test if you did the right thing, you can see the current value of the variable by doing:
```
echo $PERL5LIB
```

Does that help?
Regards.

---

### Post by cheerPuncH on 2012-05-24
It shows me the path of the second $PERL5LIB and not the first $PERL5LIB. Is that normal? I did the export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib:$PERL5LIB, which (as you said) should have added the path to the original PERL5LIB variable in the .bashrc. 

These are the two variables in my .bashrc
export PERL5LIB="/home/diltsjr/perl5/lib/perl5/i686-linux-gnu-thread-multi-64int:/home/diltsjr/perl5/lib/perl5";
export PERL5LIB=/usr/local/bin/amos-3.1.0-rc1/lib:$PERL5LIB

When I : echo PERL5LIB
I get /usr/local/bin/amos-3.1.0-rc1/lib:/usr/local/bin/amos-3.1.0-rc1/lib

Why am I not getting the other directory paths? Do you think this is contributing to my problem?

---

### Post by papibe on 2012-05-24
Well, why don't you try to join the lines into one:
```
export PERL5LIB="/usr/local/bin/amos-3.1.0-rc1/lib:/home/diltsjr/perl5/lib/perl5/i686-linux-gnu-thread-multi-64int:/home/diltsjr/perl5/lib/perl5"
```
Tell us how it goes.
Regards

---

### Post by cheerPuncH on 2012-05-25
I echo-ed and both paths came back and the script works. I'm not sure what it didn't like, but thanks for all your help. I guess the two variables were confusing it (though it shouldn't).

Best!

---

### Post by papibe on 2012-05-25
:D Great!

Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

