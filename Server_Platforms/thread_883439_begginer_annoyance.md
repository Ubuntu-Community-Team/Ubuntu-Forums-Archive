---
title: "begginer annoyance"
date: 2008-08-07
forum: Server Platforms
---

### Post by niwatori1 on 2008-08-07
ok im completly new to servers.I understand how it works and i know the basics(ports,Lamp,etc)
i can run teminal but i have webmin installed.
i want to run a basic webpage(no dynamics,Just HTML code) to prove it works
i want to have a domain name for astetics however it definatly not nessessary 
problem is i didn't insall any server software at the install so i have a bare-bone system 
i also have to configure my port because port 80 is to restricted and busy to use on my network (sharing with 4 other people).
any help at all would be cherished and used
    Thanks 
        Niwatori1

---

### Post by loligager on 2008-08-08
first just install apache2 via synaptics
then get an account with no-ip.com [this is really cool it will dynamically update your site and give you a free domain] but it will be a suckish domin
ex: [http://blablabla.no-ip.biz](http://blablabla.no-ip.biz) or [http://blablabla.no-ip.org](http://blablabla.no-ip.org)

^^ note you must create an account with no-ip.com first

Now install no-ip2 [it is a paskage
enter in your username-[email address] and password and time interval is 1
[if you have any questions ask me at ##m_newton... i will answer when i can]

Once that is done you go to /var/www and put in your index.html
it should work
Be sure to forward which ever port you are using to YOUR computer
um idont know bout the diffrent port configuration on apache so you are on your own for that
Hope i helped!!

---

### Post by cariboo on 2008-08-08
Actually no-ip has several different domains you can use. I chose xxxxxxx.servebeer.com, it works as an inside joke, and no one else knows the actual address. I had to pick something even though I only use it for ssh,sftp.

Jim

---

