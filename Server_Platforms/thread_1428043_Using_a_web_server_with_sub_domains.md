---
title: "Using a web server with sub domains"
date: 2010-03-12
forum: Server Platforms
---

### Post by ronhagley on 2010-03-12
hi all, I'm new to Ubuntu so finding some things tough. I've tried to set up an old laptop with Ubuntu server - need to use it as a web server for a group of students on a local network only.
I managed to get it working fine for just one user publishing webpages etc to a folder called VAR/WWW I could FTP files into the folder and access them again via FTP or a browser.
I then decided to create some subaccounts (one for each student)
I did this by typnig the following commands:
Sudo usermod -g www-data student1   
Sudo chown -R www-data:www-data /var/www/student1
Sudo chmod -R 775 /var/www/student1

(In this example student1 is intended to be a subfolder of www and act like a sub-domain with write authority- at least that was my intention)

Problem I then get is that if I use Filezilla to access each account I cannot see where to publish the files - wherevever I place them they are not accessible from the browser.

Do any of you experts out there know the answer to my problems please.

---

### Post by Ryan Dwyer on 2010-03-12
You need to configure Apache to use student1 as a subdomain. Otherwise it's just a folder in the main site. Also, I wouldn't put subdomains underneath the main domain like that because users could browse to it through the main domain.

To set up the subdomain, you need to:
# copy the existing vhost file
cd /etc/apache2/sites-available/
sudo cp default student1
# edit the file and change the configuration (set ServerName = student1.whatever, as well as DocumentRoot to the student1 folder)
sudo nano student1
# enable the site
sudo a2ensite student1
# restart Apache
sudo /etc/init.d/apache2 restart

You'll also need to add an entry to your local DNS server so the clients will resolve student1.hostname to the correct address.

If you want to read documentation on setting up subdomains, the correct terminology is "virtual hosts", sometimes abbreviated to vhosts.

---

