---
title: "mounting multiple /home/ dirs to /var/www"
date: 2006-10-02
forum: Server Platforms
---

### Post by Curtis_B on 2006-10-02
Hello, I searched for this topic and couldn't find anything. 

I'm setting up a small business intranet / file server. I currently have two users: curt (me) and artwork. 


I wanted to keep ftp users chrooted into their home folders, yet allow them to FTP relevent web server files. So, the first thing I did was mount --bind /var/www/ to my /home/curt/www/. That way, I can have access to everything on the webserver. (Files like phpMyAdmin are physically located in /var/www). 

All is well. Now, I want to mount the artwork to the webserver as well into a subdirectory. I made a directory /var/www/artwork/ and tried to mount /home/artwork/ to /var/www/artwork/ but the 2nd mount does not take. Through rebooting and doing these mounts in opposite order, I've determined that the order does matter, whichever mount is set first will be the only one to actually work.   

I realize I could just give in and merge the two accounts, as everything will be used for one small business, but I'd like to think that the two mounts are possible. Any help is greatly appreciated. 

Curt

---

### Post by sonic2000gr on 2006-10-02
I recreated all the steps on my vmware test server and I can't really find any problem with what you are doing. It is not a good idea to mount the /var/www directory directly into /home/artwork. Create a directory inside /home/artwork and mount it there. You may wish to have a look at the following:

- Join a common group with artwork so you can set write permissions for all the files easily. Assuming your account is curt and the other account is artwork, you may wish to join the artwork group (In ubuntu when a user account is created, a corresponding group with the same name is created as well). To add your user account to the artwork group:

```
sudo /usr/sbin/usermod -aG artwork curt
```

- Set permissions and owner for all files under /var/www:

```
sudo chown -R curt:artwork /var/www
      sudo chmod -R 775 /var/ww 
```

This way you have write access as the owner, artwork has write access as the group and everyone else has read permission (including the www-data account used by apache). When artwork creates a file in there, you will have write access since you belong to the artwork group.
The only other detail would be to set the umask for artwork and yourself so that all created files have 775 permisions.

For that edit the /home/curt/.bashrc file and add or change:

```
umask 0002
```

and also edit /home/artwork/.bashrc and add or change:

```
umask 0002
```

- Create a directory inside the home directory of artwork and mount the /var/www/artwork there, ie:

```
sudo mkdir /home/artwork/art
sudo chown -R artwork:artwork /home/artwork/art
sudo mount --bind /var/www/artwork /home/artwork/art

```

Hope this helps.

---

### Post by Curtis_B on 2006-10-02
Thanks a lot for your help, I have to leave work now, but I will definately work through this tomorrow. 

Curt

---

