---
title: "Permission of html file"
date: 2005-12-04
forum: Server Platforms
---

### Post by johnmd on 2005-12-04
I have several web pages and I have always updated them using Windows.
Yesterday I stared to use Ubuntu.
I did every thing the same as I have for years except I used Mozilla Composer.
After the files had been uploaded they could not be accessed from a browser.
I checked with my hosting service and was given the following answer.

">   Sorry for the delay in getting back to you. We have fixed your issue.
Now you can access the files
>
> [http://oldcarandtruckpictures.com/PickupTrucks/1960-1973.html](http://oldcarandtruckpictures.com/PickupTrucks/1960-1973.html)
> and [http://oldcarandtruckpictures.com/Studebaker/Hawk.html](http://oldcarandtruckpictures.com/Studebaker/Hawk.html)
>
> You have set the permission of these files to 700. But  in order to access
the pages via browser you have to set a minimum permission of 644 to the web
files.
>
> Now we have corrected the permisions. Please verify from your end."

How do I set the permission as they said I need to?

John

---

### Post by Platoxia on 2005-12-24
John, 

The way security is set up in Linux is with permissions. Apparently, when you were working on the pages on your Ubuntu system they took on the default permissions of the user you were working on them with.

Linux file permissions are set up as follows: 
[LIST=1]
[*]Owner (person who created the file)
[*]Group (users can belong to groups in order to share files amoung group members)
[*]Other (anyone else who has access to the computer)
[/LIST]

Now, I will try to explain this without being too confusing. inside each of these three groups of permissions, there are Read, Write, and Execute permissions. So in other words, you can choose who can do any combination of Read, Write, and Execute the file...amoung each of the groups (owner, group, and other).

This is a simple explanation to say the least. A good tutorial on this can be found here:

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

However, permissoins can be set in Ubuntu very easily by right clicking on the file and clicking on the permissions tab to set the permissions. The Ubuntu guide for this can be found here:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Hope this helps.

Regards

---

### Post by ninotob on 2005-12-25
Hey -- I want a rampside pickup and an amphibicar!  I'd never heard of a rampside pickup but that's brilliant!  Why don't we see those?

---

### Post by BobSongs on 2005-12-25
[QUOTE=Platoxia]<snip>The Ubuntu guide for this can be found here:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

</snip>[/QUOTE]

Or, more specifically, here:

[http://ubuntuguide.org/#changefilesfolderspermissions]("http://ubuntuguide.org/#changefilesfolderspermissions")

---

### Post by ninotob on 2005-12-25
If you are comfortable using the command line, it is faster than right clicking each file.

You can use the permisions octets (the numbers -- I never can remember them very well) or you can use letter codes.

for example:

chmod u+rw,g+rx,o+rx somefile.html

is the the same as 

chmod 655 somefile.html

with the octets, you have

1=x
2=w
4=r

you add them together to come with a number, and the three positions indicate user, group, others in that order.  So to get user=rw, you put 6 in the first position.  Group is rx, so 5, and others is rx so 5.  

For me, it's just easier to type it out longwise because I can never remember if x or r is 4, though I usually presume opposite of correctly.  ;-)

Anyway, lots of blah blah blah there.  Here's the cool part, if you have 10 files, say all of them *.html, then you can just do:

chmod 655 *.html

Saves a lot of right clicking that way.  Note, I used the octets for brevity.  Also note, with the letter codes, you can subtract permissions by replacing the "+" with a "-".

EDIT:  BTW, your site is fun -- I enjoyed looking at the pics.  You should check your stats or logs -- I bet today is a better than average day for linux hits.

---

### Post by ShirishAg75 on 2005-12-25
how to do I chmod a whole folder. First turn su & then go to /Media/D/foldername. The folder has only html files & I wanna see them without going through the whole hog of saying it's an executable file.

---

### Post by timfrost on 2005-12-25
You can do what is needed with
```

cd /Media/D/foldername
find . -type d -print | xargs chmod 755
find . -type f -print | xargs chmod 644

```
This gives group/other read permission everywhere, and search permission on directories.

Specal treatment may be required if there are any CGI scripts. (They need "chmod 755" to get execute permissions in the web server.)

---

### Post by johnmd on 2005-12-25
Thanks everyone but I sat down and scratched my head a bit and figured out what had happened.
I changed the permission and all is well.
I did it by right clicking on the file and selecting "permission" and changing it there.
There is quite a learning curve for an old guy like me but I think it's worth it.
I still have completely switched over yet because I need a faster computer then the  P III 500 this I have it installed on.

That rampside was a good idea but was only used on the Covair rear engine model.
It was a bit difficult to have a rear ramp when the engine was back there.
Once the Corvair was gone so was the side ramp.
You have to remember that GM is one of the most brilliant auto makes around. That's why they have gone almost bust.


John

---

### Post by ShirishAg75 on 2005-12-25
This is the error I'm getting even though I'm a superuser here. 

```
 root@ubuntu:/media/D/Ubuntu Stuff_CD# find . -type d -print | xargs chmod 755
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
chmod: cannot access `./Ubuntu': No such file or directory
chmod: cannot access `guide': No such file or directory
chmod: cannot access `stuff.php_files': No such file or directory
``` 

         If I try the same with the f difference this is what I get :-

root@ubuntu:/media/D/Ubuntu Stuff_CD# find . -type f -print | xargs chmod 755
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
chmod: invalid option -- d
Try `chmod --help' for more information. 
    
As far as I can see there are no quotes anywhere. I looked hard to see but couldn't see any typos anywhere.

---

