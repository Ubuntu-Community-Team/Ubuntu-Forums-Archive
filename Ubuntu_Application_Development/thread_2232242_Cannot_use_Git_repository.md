---
title: "Cannot use Git repository"
date: 2014-06-30
forum: Ubuntu Application Development
---

### Post by rompelstilchen on 2014-06-30
hello

i try to use a git server i just installed

the install and project config worked fine, i used these commands :

```

sudo apt-get install git-core
git config --global user.email "my@mail.com"
git config --global user.name "myuser"

cd /media/hd2
mkdir Project
git init --bare Project/
 

```

but the access from the same machine does not work
i also tried from another machine under netbeans, it cant find my repository

```

cd /home/myuser/Desktop/
git clone myuser@***.***.***.***/Project
git clone myuser@***.***.***.***:/Project
git clone myuser@***.***.***.***:/Project
git clone myuser@***.***.***.***:Project
git clone myuser@$***.***.***.***:$Project.git
git clone myuser@$***.***.***.***:$Project
git clone myuser@$***.***.***.***:$Project.git
git clone myuser@***.***.***.***:Project
git clone myuser@***.***.***.***:GIT/Project
git clone myuser@***.***.***.***:Project
git clone myuser@***.***.***.***:Project
git clone myuser@localhost:Project

```

***.***.***.*** = the ip of the server

i always get the same error

```

Cloning into 'Cortex'...
ssh: connect to host localhost port 22: Connection refused
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

```


can anyone help me
everyone says it is supposed to be simple but this s@#t is really getting on my nervs

thanks

[edit] I installed ssh , the official doc didnt say anything about that
anyway it seems the git server does not recognize my Project as a repository

```

git clone myuser@***.***.***.***:Project
Cloning into 'Project'...
myuser@***.***.***.***'s password: 
fatal: 'Project' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.


```

---

### Post by rompelstilchen on 2014-06-30
ok for those who have the same issue
i had to use the full path of the repository 
jesus...
WTF raised to power of 10

---

