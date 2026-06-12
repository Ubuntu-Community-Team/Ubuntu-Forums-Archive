---
title: "Working on building a local ad hoc wireless community"
date: 2013-09-07
forum: The Cafe
---

### Post by ki4jgt on 2013-09-07
I'm working on building a local ad hoc wireless community called Bluenet. The plan is to provide a local messageboard/file sharing service/chat/news blog. So, I've gotten dd-wrt in ad hoc mode with OLSR protocol and redirected all DNS requests to a single server on the network.

Here's a copy of the site files: [https://dl.dropboxusercontent.com/u/23080006/Bluenet-9.13%20%28ALPHA%29.zip](https://dl.dropboxusercontent.com/u/23080006/Bluenet-9.13%20%28ALPHA%29.zip)

Which is also capable of having addons. To test it out, simply python -m CGIHTTPServer 8000 out of the main folder. Instructions to create add-ons are in the README file and I haven't built any addons yet so all you'll see is an introduction to the service for visitors. I've created a community for it at buckysroom (for everyone who knows what that is). It isn't finished yet but the modular addons will hopefully allow other devs to add their own services. Thanks guys.

---

