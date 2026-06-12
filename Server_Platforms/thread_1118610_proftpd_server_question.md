---
title: "proftpd server question"
date: 2009-04-07
forum: Server Platforms
---

### Post by fouadk on 2009-04-07
hi everyone...

i have setup proftpd as a standalone server...i have created some users with /bin/false as login shell and i have setup home directories in apache....

my purpose is that users ftp to the server and then using there username and password login and automatically be directed to their home folder...i currently have one user and this conf file obviously works for a one user only....

second of all when i change directory to /home/eliomassih/public_html/ , i cant delete the files in it...i cant figure out why???

please help

Thanks in advance

this is my conf file
```


# Set the user and group that the server normally runs at.
User                  ftp
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/eliomassih

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser eliomassih
DenyALL
</Limit>

<Directory /home/eliomassih>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory> /home/eliomassih/public_html/*>
Umask 022 022
AllowOverwrite on
AllowAll
</Directory>



```

---

### Post by loudog23 on 2009-04-08
Here is the answer to all your question: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

check this post for multi-user folder: [http://ubuntuforums.org/showpost.php?p=7027404&postcount=992](http://ubuntuforums.org/showpost.php?p=7027404&postcount=992) (My post :P )

Here is the list of Limit you can put and what they mean: [http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-FTP-commands.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-FTP-commands.html)

Here is the correction for your .conf files:
> <Directory> /home/eliomassih/public_html>   # **<- I REMOVED THE /***
Umask 022 022
AllowOverwrite on
**<Limit>**
AllowAll
**</Limit>**
</Directory>
Thinking of it twice, i bet you could just remove the limit section and it would work for you. (hey im a newb too)

Full access to the folder:

<Directory> /home/eliomassih/public_html> #Directory permission(no /*)
AllowOverwrite on 
**<Limit>**                            # <Limit 'InsertCommandHere'>
AllowAll                                  # Allow or deny access to the limit set on previous line
**</Limit>** #Close limit switch
</Directory> #Close directory setting

So you can set different Allow or deny different permmission in the same directory. (in example you will be able to **M**a**k**e**D**irectory but not **R**e**m**ove**D**irectory

<Directory> foldername
AllowOverwrite on
<Limit MKD> #create folder
AllowAll #Allow command
</Limit> # Close limit

<Limit RMD> #remove Folder
DenyAll #Deny command
</Limit> #Close Limit
</Directory> #close directory section 

Ive notice that by removing the '/*' set the limit to the folder itself.

Also Make sure your local permission is set properly.
Term window:
'sudo chown ftpusernamehere ftpuserfolderhere"
and set permission to 755
'sudo chmod 755 ftpuserfolderhere'
i've set permission to 700 so even local user cannot access the folder without re'sudo chown'ing them back. This way only ftpuser can have access to the folders.

Enjoy !!!

):P :guitar:

Now, please tell me how i can create a website on my computer and link it to my already "up" ftp server (on the same machine). In a way that users can type 'www.mywebsite.com' and get into a website (with different links, pitures, blogs) with a link to the ftp.

Is that the same? apache and proftpd? like you did?

Thank you back :D
lou

---

### Post by fouadk on 2009-04-09
Dear Sir,

Thanks a lot for the effort you put in writing your reply...it was very helpful...

however im still having a small problem.

the following directory tag which is responsible for the folder /home/eliomassih is working just fine because in that folder i cannot upload neither files nor folders, which is exactly what i want....

```

<Directory /home/eliomassih>
Umask 022 022
<Limit RMD MKD DELE STOR STOU>
DenyAll
</Limit>
</Directory>

```


but the following directory tag which is responsible for /home/eliomassih/public_html is not working as i want it to because i cannot upload any files or folders to that directory.

```

<Directory /home/eliomassih/public_html>
Umask 022 022
<Limit MKD RMD STO STOU DELE>
AllowAll
</Limit>
</Directory>

```

why is that happening?even though it is set to AllowAll on MKD RMD STO DELE

please help.
Thanks in advance

concerning your question...i did not fully understand what you wanted....please elaborate...i will be glag to help you

---

### Post by loudog23 on 2009-04-09
> **fouadk said:**
> Dear Sir,

Thanks a lot for the effort you put in writing your reply...it was very helpful...

however im still having a small problem.

the following directory tag which is responsible for the folder /home/eliomassih is working just fine because in that folder i cannot upload neither files nor folders, which is exactly what i want....

```

<Directory /home/eliomassih>
Umask 022 022
<Limit RMD MKD DELE STOR STOU>
DenyAll
</Limit>
</Directory>

```


but the following directory tag which is responsible for /home/eliomassih/public_html is not working as i want it to because i cannot upload any files or folders to that directory.

```

<Directory /home/eliomassih/public_html>
Umask 022 022
<Limit MKD RMD STO STOU DELE>
AllowAll
</Limit>
</Directory>

```

why is that happening?even though it is set to AllowAll on MKD RMD STO DELE

please help.
Thanks in advance

concerning your question...i did not fully understand what you wanted....please elaborate...i will be glag to help you

I had the same problem as you yesterday night, and then i found out that the permission set into the .conf is recursive and bottom layer folder have priority.

In your case since youve put '/home/eliomassih' in DenyAll, this permission is overtaking the '/home/eliomassih/public.html' persmission.

The only way i see would be to remove the section about '/home/eliomassih' and rely on local permission to prevent WRITE to the folder.

this works for me. now how safe it is? i dunno but one of my friend tried to get in and bypass those permission without success.


As for my question, i found most of the answers on this forum. But if you can give me some input it would be nice.

I've created a ftp so my friend can store and backup files into my pc. But since most of them don't even know what a FTP is. 

So to make it simple for them i want to create a web-page (with apache) and link the FTP to the page in a way that they just have to type [www.mywebpage.com](www.mywebpage.com) and go to the upload/donwload section.

The ideal situtation would be:
-Webpage with a login box.
-Once they are logged-in, have an upload/download page so they can send and receive files without an ftp-client.
-Is this doable? for now i've set an web-page with an link to [ftp://myftpsite.com](ftp://myftpsite.com).

Sorry my english is far from being perfect. hope it is a bit clearer.

I feel like we are doing exacly the same thing except that you have the Apache part done and working on the ftp side, and I have the ftp part done but need to set Apache. :P

Hope this will help you. I suggest you read the link i provided you (answer to all your question) I know it's 11 pages long, but alot usefull info is in there.

Enjoy, take care,
lou

---

### Post by fouadk on 2009-04-09
thanks a lot again for the time you spent on writing the reply...

concerning  your question....i hope i understood what you meant...
what you basically want to do is :
1-user get to a login page
2-once logged in,  they have an upload and download section where they can upload and download files....

my question to you is the following:
are you taking care of uploads and downloads through ftp???

if i were you i would have done it through php.
i would create one folder where you upload and download files from and to.
you can find millions of php upload examples on how to upload files to a server,,,,

if you find that helpful let me know or i will try to help you in every other possible way.

Thanks a lot again

---

