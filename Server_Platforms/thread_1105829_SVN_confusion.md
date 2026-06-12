---
title: "SVN confusion"
date: 2009-03-25
forum: Server Platforms
---

### Post by twistedtwig on 2009-03-25
Hi all,

I am in the process of setting up Subversion on my main Ubuntu box.  This box already has apache running which hosts 3 websites.

I am gettiing a bit confused with a number of things and was hoping people might be able to help straight it all out for me.

I have a mix of systems at home.  I use Ubuntu as my system, have an XP VM for VS2008 and a 2003 server.  I mainly develop in C# at the moment.

My goal is to be able to have the repository on the Ubuntu server, be able to access it securely (logging in, can not do SSL because of another project), across the net ideally.  Also want to be able to use tortoisesvn or the like to access the reposotories via the LAN.

I have subversion in and during one of the install guides it guided me to create a testing.txt file in one of my projects.  If I do the tree look command thingy (can't remember it at this moment), I can see the file in the repos.

I have Trac and Websvn installed.

1) Trac seems to be a way of just monitoring what has happened in the project, have a basic wiki for it and create tickets for issues, is this right?

2) Websvn seems to be a read only way of accessing the repos, is this right?

3) How do I get tortoisesvn to connect via the LAN?  my repos are at /var/svn-repos/project_project1

4) How do I create more repositories?  Do I have to go via the command line on the server it self?

5) Is it the norm to have one main repository and then create different projects under that repository?

6) When I typed svnserve -d I believe that started the standalone svn server app on the Ubuntu server, I then seemed to be able to get tortoisesvn to connect and get out the text file I created.  I altered it but when I tried to commit I always got an "authentication" error.  Should I be using svnserve, I thought there was a web extension of some kind that allowed tortoisesvn and the like to communicate with the server.

Thank you for all your help and support.

I have trac and websvn setup in a subdomain 

sub.example.com/websvn
sub.example.com/trac

if I go to the URL below I get a site that shows:

Collection of Repositories

    * project_project1/
    * project_project2/

Powered by Subversion version 1.4.4 (r25188).


example.com/svn/

---

### Post by twistedtwig on 2009-03-25
Would anyone be able to help me with this please?  I am rather confused with Subversion and how someone might be able to answer some or all of the questions.

Thank you.

---

### Post by twistedtwig on 2009-04-07
Hi all,

I am still stuck with this.. I hope someone might be able to help me.

Thanks

---

