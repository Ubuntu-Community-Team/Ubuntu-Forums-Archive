---
title: "How to secure all under /var/www/ except for one dir"
date: 2007-05-18
forum: Server Platforms
---

### Post by tbuss on 2007-05-18
I have a website set up using apache2. I have configured the site for username and password for everything inside /var/www/ using this:
```
<Directory /var/www/>
AllowOverride AuthConfig
AuthType Basic
AuthName "Family FIles"
AuthUserFile /home/secure/apasswords
Require valid-user
</Directory>
```
This works as advertised but I would like to single out a single directory located in /var/www/ that this does not apply to, so that users can connect without autho but at the same time are not able to browse to the other files located in the same directory.

---

### Post by craigp84 on 2007-05-18
Hi tbuss,

If i'm reading you right, then no, there's no simplistic way to do this.

Consider splitting out your data into another structure whereby the public and private files are seperate branches. You can then use symlinks from the private folder structure to point to the public stuff.

The end result is indistinguishable from your goal to the user, only we know the secret sauce that makes it work :-)

Hope this helps,

-c

---

### Post by tbuss on 2007-05-18
> Consider splitting out your data into another structure whereby the public and private files are seperate branches. You can then use symlinks from the private folder structure to point to the public stuff.
I'm not sure I follow.

My files are structured as such:
```
tbuss@homeServer:/var/www/family$ ls
musik.html                                      
noggin.html                 
photos.html
chat.html                     
contact.html                  
games.html                       
index.html
video.html
pictures            
game                                     
style                  
video
jS                            
music
```
All of these under var/www/family/ are username and password protected. Are you suggesting creating a dir to place the "public" files in and then creating a link that would bypass the autho for the rest of the site? I apologize in advance, I have not been doing this very long.

---

### Post by ricrac on 2007-05-18
Many ways to do this, a simple one would be to add another dir for public use.  You can add as many as you like, each with it's own auth settings.  
```

<Directory /var/www/>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "Family FIles"
  AuthUserFile /home/secure/apasswords
  Require valid-user
</Directory>
<Directory /var/www-public/>
  AllowOverride None
  Order allow,deny
  allow from all
</Directory>

# as many more as you need, for example
<Directory /var/www-personal>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "My Personal Files"
  AuthUserFile /home/secure/MyPersonalFiles-passwords
  Require valid-user
</Directory>

```

You can set overlapping rights, global for a dir, then specific for a subdir.
However, using different parent dirs is generally easier to maintain, which is one reason why cgi-bin is a top level directory that is script aliased in to look like it's under the docroot.

---

### Post by craigp84 on 2007-05-19
Ricrac, thanks for repeating what i said.

Tbuss,

Go with something really common. Go with a "public" site, with a private family folder. It's easier to use for non family members.

If you want to hide the fact a dir exists, but not password protect it, then just don't link to it from index.html.

No special setup in apache required (short of the username / pw stuff you already have on family/).

/var/www/
                ->
                    index.html
                    family/
                             ->
                                  game/
                                  video/
                    public_file1.html
                    public_folder/

-c

---

### Post by tbuss on 2007-05-19
craigp84,
> Go with a "public" site, with a private family folder
Okay, but I have to ask. I'm not dense, just having trouble grasping the concept. I'm not trying to hide the public_folder/ from the family/, I want to hide the family/ from the general public . So on the public_file1.html all I need to do is not include any links to the private folders. You had placed the public_file1.html under /var/www/ and my config file has everything under /var/www/ protected. So there is no way for any one to browse from the public to the private without autho? But users can browse from private to public if I create a link?

If I understand this correctly, all I'm doing is creating 2 index.html files (index.html and public_file1.html) under var/www/
One will be for private use and the other for public
My config file is set up for autho for everything under /var/www/, will this not apply to the public_file1.html as well, or did you illustrate for it to be placed elsewhere:

/var/www/
->
index.html
family/
->
game/
video/
public_file1.html
public_folder/

Are you suggesting something like this?
 ```
/var/www/family/all/private/files/go here/ 
/var/www/public/all/public/files/go here/
```
```

<Directory /var/www/family/>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "Family FIles"
  AuthUserFile /home/secure/apasswords
  Require valid-user
</Directory>
```

Like I said, I'm very new to this. I'm going to try as you suggested, when I'm done I'll give you a link if your interested.

---

### Post by ricrac on 2007-05-19
craigp84,  You're welcome.
If you notice the time stamps you'll see we posting at the same time.  Your post wasn't there when I wrote my reply.

Two dirs
/var/www   -  is public with no auth needed
/var/www-family - is private with auth required
/vaw/www/index.html  - is a public file without any reference to www-family
/vaw/www-family/index.html  - is a private authenticated file with a reference to /var/www/index.html

See dir's flop-flopped from earlier post to make www public and www-family private
```
<Directory /var/www/>
  AllowOverride None
  Order allow,deny
  allow from all
</Directory>
<Directory /var/www-family/>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "Family FIles"
  AuthUserFile /home/secure/apasswords
  Require valid-user
</Directory>
# as many more as you need, for example
<Directory /var/www-personal>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "My Personal Files"
  AuthUserFile /home/secure/MyPersonalFiles-passwords
  Require valid-user
</Directory>
```


Or using a single parent dir

/var/www   -  is public with no auth needed
/var/www/family - is private with auth required
/vaw/www/index.html  - is a public file without any reference to www-family
/vaw/www/family/index.html  - is a private authenticated file with a reference to /var/www/index.html

See dir's flop-flopped from earlier post to make www public and www-family private
```
<Directory /var/www/>
  AllowOverride None
  Order allow,deny
  allow from all
</Directory>
<Directory /var/www/family/>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "Family FIles"
  AuthUserFile /home/secure/apasswords
  Require valid-user
</Directory>
# as many more as you need, for example
<Directory /var/www/personal>
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "My Personal Files"
  AuthUserFile /home/secure/MyPersonalFiles-passwords
  Require valid-user
</Directory>
```

Not referencing directories does very little to protect them, use auth if you need restrictions.
Brute force can locate any non-referenced directory.

---

