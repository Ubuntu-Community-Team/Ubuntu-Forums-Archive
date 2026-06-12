---
title: "How to open a virtual host with http or https"
date: 2012-04-10
forum: Server Platforms
---

### Post by starz677 on 2012-04-10
Hello,

Having read what seems like every page available on the Internet on this....(small exaggeration) I'm still stumped.

I have a working ubuntu 10.04 server with apache2 .
I have 2 virtual hosts
SSL is tested and working on the server
When I try to open either site with https, it only looks in the Root of the web directory

I can open both sites using http but would like to be able to access both sites with http or https

What I can't figure out is how to add port 443 access to those same virtual hosts.

In /etc/apache2/sites-available I have both virtual hosts in their own <Virtualhost *:80> container
It stands to reason that I need a <Virtualhost *:443> duplicate container (file) for the https access but that doesn't work and it seems awkward having two identically named files in the sites-available folder.

I also tried changing the <Virtualhost *:80> line to <Virtualhost *:80 *:443> but that failed.
I also tried changing the <Virtualhost *:80> line to <Virtualhost> and that also failed

Finally, I tried copying a duplicate of the Virtualhost file for the site into ssl.conf and added a directive to include ssl.conf to Apache2.conf (changing virtualhost *:80 to Virtualhost *:443>......that also failed.

If I change the <Virtualhost *:80> line to <Virtualhost *:443>  it works.  But I want to be able to open the site secure or unsecure.

Not sure what to do.

Thanks


[SIZE=4][COLOR=Green][B]Never mind.   Found the solution.  ):P
Just include the SSL directives inside the Virtual host file.
[/B][/COLOR][/SIZE]

---

