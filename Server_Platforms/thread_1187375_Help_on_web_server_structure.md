---
title: "Help on web server structure?"
date: 2009-06-14
forum: Server Platforms
---

### Post by lian1238 on 2009-06-14
Hi all! I hope this is an appropriate place to ask.

I'm at a lost choosing a server-side scripting language. What I'm trying to create is an intermediate web application with Adobe Flex (as to learn how to use it). This application will be hosted from my own home computer (ubuntu 8.10 desktop edition) with apache set up.

The application will do the following:

[LIST]
[*]get user input and send a request to the host server (my University's course look-up page)
[*]Retrieve/manipulate/display the result
[/LIST]
What's done:

[LIST]
[*]I've written a script in python to POST a query to the host server using BeautifulSoup
[*]from the terminal, the script is able to extract needed information from the result of the query
[/LIST]
My problem now is this:

[LIST]
[*]Adobe Flex does not run python scripts directly
[*]My apache server does not run python scripts
[LIST]
[*]I've installed mod_wsgi but do not know how to use it.
[/LIST]
[/LIST]
Suggestions/help are welcome.

---

