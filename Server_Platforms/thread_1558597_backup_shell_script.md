---
title: "backup shell script"
date: 2010-08-22
forum: Server Platforms
---

### Post by Vegan on 2010-08-22
OK I have a command in a file, made it executable but it does not want to work.

#!/bin/sh

tar -cvpzf backup.tar.gz /www

---

### Post by surfer on 2010-08-22
```
#!/bin/bash

/bin/tar -cvpzf backup.tar.gz /www

```

this works for me.

---

### Post by Vegan on 2010-08-22
I find I have to invoke it with

sudo bash save

so what do I need to do to not need to call bash or is that needed?

---

### Post by CharlesA on 2010-08-22
You would need to run it with ./script.sh

---

### Post by Lars Noodén on 2010-08-23
> **Vegan said:**
> I find I have to invoke it with

sudo bash save

so what do I need to do to not need to call bash or is that needed?

What does **ls -lh** say you have for file permissions?
It needs to have the correct permissions to run.  

```

chmod +x */usr/local/bin/*save

```

Also, inside the script it is a good idea to either use absolute paths or set **PATH** explicitly at the beginning.

```
*/bin/tar*
```

---

### Post by Vegan on 2010-08-25
The script is set to executable, right now I am using sudo bash save to invoke manually, I wanted to better mechanize it so I can symlink it to a cron job

---

### Post by CharlesA on 2010-08-25
I don't understand why you need to use "sudo bash save." You should be able to run it from the pwd by issuing:

```
sudo /path/to/script
```

Or use this if it's in the pwd.

```
sudo ./script
```

Try this:

```
#!/bin/bash
echo "hello world"
```

Dump that into a script, make it executable and then run it with ./script

---

### Post by TwoEars on 2010-08-25
The reason why you can't just use save is because it's not added on the system path. Run this command```
echo "#!/bin/bash" | sudo tee /usr/local/bin/save && echo "/bin/tar -cvpzf backup.tar.gz /www" | sudo tee -a /usr/local/bin/save && sudo chmod +x /usr/local/bin/save && sudo ldconfig
```

Or in simpler terms -
```
echo "#!/bin/bash" | sudo tee /usr/local/bin/save
echo "/bin/tar -cvpzf backup.tar.gz /www" | sudo tee -a /usr/local/bin/save 
sudo chmod +x /usr/local/bin/save
sudo ldconfig

```

The top "#!/bin/bash" bit is known as the shebang, the /bin/bash bit tells the system which interpreter to use in order to run the file, which is why you don't need to say bash save every time.
tee edits a file, tee -a appends a string to an already existing file.
chmod +x makes the file executable.
ldconfig ensures all the needed links have been made.

Now you can run save from anywhere, without needing to say "bash save", of course, the sudo is still needed, so ```
/usr/local/bin/save
``` would be the command to put into cron, but, this is just a line - I do not understand why you would wish you create a file to do this anyway, when ```
 crontab -e
``` then putting in ```
/bin/tar -cvpzf /backups/backup.tar.gz /www
``` with the needed user and time/date settings will do.

---

### Post by CharlesA on 2010-08-25
Wow, I took that as a literal command. *headdesk*

---

