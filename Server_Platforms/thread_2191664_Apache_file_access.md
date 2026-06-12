---
title: "Apache file access"
date: 2013-12-03
forum: Server Platforms
---

### Post by monkeybrain20122 on 2013-12-03
Hi,

I am in the process of writing a web application using R (the statistical package) and  Rapache [http://rapache.net/](http://rapache.net/) with brew (an R package which allows one to mix html with R code)
Now I can create a plot but I am not sure where to output it. The problem is R cannot write to the webroot (/var/www/) without changing permission and Apache cannot access file outside the webroot.
There seems to be two possibilties

1) change the permission of /var/www. Some people suggested chmod 777 . This is ok for development but I think it is undesirable for real deployment because of security issues. I need to think about real deployment as this will eventually be for production. Are there other more acceptable permission combo if I want to pursue this route?

2) Have R outputs the graph to a different folder outside of the webroot and allow www-data to access the folder

 R is able to write to /tmp to generate a temporary file for the plot, but Apache cannot access /tmp. Is it possible and advisable to allow ww-data to access /tmp? (I try to make the web app as independent of particular architecture of the file system as possible) 

How does Alias fit in if I use approach 2)? 

php is not supported by brew, and I am told that it is not needed for this purpose.

I am new to web and Apache. Hope that the questions make sense. Thanks in advance for any advice.

---

### Post by volkswagner on 2013-12-03
What user does R operate under. You can check the /tmp files created by R if you don't know the user.

You can then add the R user to the www-data group.

---

### Post by monkeybrain20122 on 2013-12-03
I am not sure if I should modify www-data. It seems that if I just allow www-data to access a particular folder where R outputs the graphs (either /tmp or some other directory) it would be less disruptive than modifying www-data. Does it make any sense?

---

### Post by volkswagner on 2013-12-04
I fail to see the difference.

/tmp is not a good directory to store items you want to keep.

Regardless if you have your webroot set to /var/www, /home/webuser/html or /mynewwebsite, both locations will need to be writeable by both www-data and R.

Depending which user you trust more (www-data or R), you can decide if you want to add www-data to R's group or add R to www-data's group.

If you are seeking isolation for this one site that uses R, I can understand.

---

### Post by monkeybrain20122 on 2013-12-04
Hi,

Maybe I am a bit off. But you see, I am not responsible for setting up or maintaining the server. It is a part of a huge project. My idea is to make it so that it requires as little disruption as possible. It seems to me that changing permission to the webroot is rather serious and I don't know the ins and outs of server security  and the SELINUX rules pertaining to it (they use Centos)  so I would want to avoid it. 

It seems to be less disruptive if they just set up a folder somehwere (that R can access) for R to output to and allow www-data to access it. It doesn't have anything to do with R really, it is like serving pictures or whatever on the web outside of the web root. It seems to be a better idea than to change access to the /var/www

The outputs are only needed for displaying on the web on a per session basis so they don't need to be saved. Since R can access the /tmp directory and it doesn't require setting up a seperate folder (and hard coding the path)  I am thinking may be R should write to /tmp and apache fetches the ooutput from there.  So would it be possible to allow www-data to acess temp and would it be risky?

Thanks.

---

### Post by monkeybrain20122 on 2013-12-06
Any thought?

---

### Post by nerdtron on 2013-12-07
If your're not responsible for maintaining/administering the server, you should contact the system administrator for help. Understanding permissions can be a bit tricky for people who are new to it.
I agree with volkswagner idea to add R into the www-data group so that it will be able to read/write on the directories of apache/www-data user.

I tell you, when I setup a test server for web devs, they do chmod -R 777 on the folder where they deploy the htmls. It really is a bad idea so when it comes to production, we review the permissions first.

BTW: oh yeah, why not setup a test server first (even on a VM) and see if you method works. It won't hurt, at least you'll be sure once you do it in a productions machine. Always test before committing on a production server.

---

### Post by monkeybrain20122 on 2013-12-08
> **nerdtron said:**
> If your're not responsible for maintaining/administering the server, you should contact the system administrator for help. Understanding permissions can be a bit tricky for people who are new to it.

Since these are external contractors we need to pay them for setting up meetings, so I am trying to be as prepared about the options before I contact them (have to be done through my boss)



>   oh yeah, why not setup a test server first (even on a VM) and see if you method works. It won't hurt, at least you'll be sure once you do it in a productions machine. Always test before committing on a production server.

Oh I know it works. I have set it up on the server if R is given the permission to access www. I am trying to see if there is another way that may be able to avoid changing access right to www and whether it would be more desirable if possible.

---

### Post by bigmonmulgrew on 2013-12-09
If you need R to access www-data files and www-data to access R files.

I think your going to have to change access rights to some degree.

If your trying to avoid giving one access to all of the files of the other you could try creating a new group "www-dataR"

Then add both www-data and R to the www-dataR group. 
Change the access rights on any files they need to share to be owned by www-dataR both would have access to them but neither would have access to the others other files. Seems a little long winded though and could cause problems with new files if they get created owned by www-data or R rather than the shared group.

---

### Post by SeijiSensei on 2013-12-09
(If this is CentOS, the apache process is owned by user "apache" not "www-data".  Also, on CentOS and other RedHat-flavors, the default web directory is /var/www/html, not simply /var/www.)

What user owns the R process that generates the graphs?  Can the job be run by the apache user?  Wouldn't that solve the problem?

I usually put such files in a separate directory under /var/www to which all relevant users have rights.  If your site uses PHP sessions, you might have a /var/lib/php/session directory to which root and apache have rights.  I sometimes stash files there as well.

---

### Post by monkeybrain20122 on 2013-12-09
> **bigmonmulgrew said:**
> If you need R to access www-data files and www-data to access R files.

I think your going to have to change access rights to some degree.

If your trying to avoid giving one access to all of the files of the other you could try creating a new group "www-dataR"

Then add both www-data and R to the www-dataR group. 
Change the access rights on any files they need to share to be owned by www-dataR both would have access to them but neither would have access to the others other files. Seems a little long winded though and could cause problems with new files if they get created owned by www-data or R rather than the shared group.

Ok, let's forget about R. In my second scenario (2 from the first post) R just outputs to some folder outside of the webroot. Basically I want Apache to have access to it. But as a general question it has nothing to do with R, the folder in question may as well contain your family picture collection. 

Now there are two sub scenarios

A) It may be a fixed folder which I create. In that case I think just allow www-data to access the folder (or apache in Fedora/Centos)
B) It is the system's /tmp directory. I am wondering if it is possible or desirable to allow www-data to access /tmp so that apache can fetch files from it.

Thanks.

---

### Post by monkeybrain20122 on 2013-12-09
> **SeijiSensei said:**
> 
I usually put such files in a separate directory under /var/www to which all relevant users have rights.  If your site uses PHP sessions, you might have a /var/lib/php/session directory to which root and apache have rights.  I sometimes stash files there as well.

I think that is what the system admin told me last time we spoke, but it strikes me as not very elegant in that it depends too much on the system's architecture. I am interested in using /tmp because it doesn't need to be hard coded according to the particular folder relationship inside the webroot, and I don't need to save the outputs.

---

### Post by nerdtron on 2013-12-09
The /tmp directory which is readable by all, as it implies, stores only temporary files and I believe its contents are flushed when you reboot. Not a good idea to store files.
I think you scenario A is a possible fix, as long as you can configure apache or www-data to look into that directory.

---

