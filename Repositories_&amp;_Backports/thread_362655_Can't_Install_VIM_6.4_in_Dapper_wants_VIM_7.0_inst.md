---
title: "Can't Install VIM 6.4 in Dapper wants VIM 7.0 instead"
date: 2007-02-15
forum: Repositories &amp; Backports
---

### Post by mowestusa on 2007-02-15
This is weird, and I have no idea what I did differently. I have two dapper computers. One has VIM 6.4 and GVIM 6.4 installed and running fine.

Somehow I got VIM 7.0 installed on my other dapper install. I don't remember how I got this other than perhaps typing "sudo apt-get install vim" once to see if I had the latest version.

Now I understand that I shouldn't be able to get VIM 7.0 on a dapper install without backporting. I read posts about backporting and I know I did not do that.

I first did "sudo apt-get remove vim"

Then I tried to reinstall thinking that it would install the 6.4 version, but I got the following error.

ome@home:~$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vim: Depends: vim-common (= 1:6.4-006+2ubuntu6) but 1:7.0-035+1ubuntu1~backport2 is to be installed
       Depends: vim-runtime (= 1:6.4-006+2ubuntu6) but 1:7.0-035+1ubuntu1~backport2 is to be installed
E: Broken packages

What do you recommend I do to fix this issue?

---

### Post by andrew.46 on 2007-07-08
Hi,

 Sounds more than a little odd! You can usually uninstall vim by typing:

```
sudo apt-get remove --purge vim
```

 Vim 7 runs well on Dapper, I am running it this way with no problems. I downloaded the source and compiled as follows:

```
cd Desktop
wget ftp://ftp.vim.org/pub/vim/unix/vim-7.1.tar.bz2
tar -xjvf vim-7.1.tar.bz2
cd vim71
./configure
make
sudo checkinstall -D
```

 You will of course need compiling tools:

```
sudo apt-get install build-essential checkinstall
```

You may need to chase up a few dev files, ./configure will complain to you about this! The package usually missing is:

```
sudo apt-get install libncurses5-dev
```



                  Andrew

---

