---
title: "Setting up flask/nginx/uwsgi following a tutorial, some issues."
date: 2014-06-03
forum: Server Platforms
---

### Post by andygmb on 2014-06-03
[COLOR=#333333][FONT=Tahoma]I'm rying to set up flask/nginx/uwsgi on ubuntu following this tutorial: [/FONT][/COLOR]

[http://conra.dk/2012/05/06/flask-uws...nx-ubuntu.html]("http://conra.dk/2012/05/06/flask-uwsgi-nginx-ubuntu.html")

[COLOR=#333333][FONT=Tahoma]On trying to follow this line:[/FONT][/COLOR]

[COLOR=#333333][FONT=Tahoma]To configure uWSGI to run as a daemon, you first want to create a separate uwsgi user:

sudo useradd -c 'uwsgi user,,,' -g nginx -d /nonexistent -s /bin/false uwsgi
[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]I get "useradd: group 'nginx' does not exist" back[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]
How can I create the nginx group properly?[/FONT][/COLOR]

---

