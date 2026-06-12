---
title: "Modified HOSTS file"
date: 2009-01-28
forum: Security
---

### Post by ToyotaGuy23 on 2009-01-28
In the past, I have used a modified HOSTS file in windows systems to block ad servers and other unwanted websites.  Basically, there is a central 'blacklist' that is updated from time to time, and this 'blacklist' redirects the bad sites / servers to 127.0.0.1

I would like to modify my ubuntu HOSTS file in the same manner, but there are so many lines, that manual editing would be VERY time consuming.  

I was suggested to 'run that HOSTS file through sed' and put it into mine, but I am not familiar with this program.  

For further reading on the modified HOSTS file that I am speaking of, check out [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

I have used this strategy in the past, and it worked out nicely.  

Thanks

---

### Post by lykwydchykyn on 2009-01-28
As far as I know, the hosts file is the same on Linux and Windows (they both inherited their networking stacks from BSD Unix), I'm not sure what you'd need to do with "sed", except maybe change the endline characters (which may not be necessary).  Just copy and paste the contents from the downloaded file to your /etc/hosts file and it should work fine.   Or if you want to get fancy at the CLI:

```

sudo aptitude install tofrodos
sudo -s
cat downloaded_file.txt |fromdos >> /etc/hosts
exit

```

---

### Post by ToyotaGuy23 on 2009-01-28
You're Awesome!
Thank you!

---

