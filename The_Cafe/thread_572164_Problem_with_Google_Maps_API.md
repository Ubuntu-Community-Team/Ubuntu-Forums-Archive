---
title: "Problem with Google Maps API"
date: 2007-10-10
forum: The Cafe
---

### Post by Simple Man on 2007-10-10
Hello everyone!
I have a little Question to the Google Maps API. I hope someone can help me!

I'm making a Website with available bandrooms in Switzerland. Now, i'd like to show the visitor every bandroom that is in a compass of 20km from his home.

the coords of the bandrooms are stored in a database. Is it possible to show them? Does the Google Maps API bring us a function that makes it easier?

Thank you

Regards,
Simple Man

[SIZE="1"]Excuse my bad english... :s[/SIZE]

---

### Post by Jussi Kukkonen on 2007-10-10
It's possible. The points do not magically jump from the database to the map of course, you'll need to read from db and create the markers. Maps API has decent documentation: [http://www.google.com/apis/maps/documentation/index.html](http://www.google.com/apis/maps/documentation/index.html), start there.

If the documentation and examples do not answer your question (they really should), there's also a discussion group (probably a better place to ask Google Maps questions) : [http://groups.google.com/group/Google-Maps-API](http://groups.google.com/group/Google-Maps-API)

---

