---
title: "I made a site generator/manager. Would love for people to test it out on Ubuntu"
date: 2019-08-08
forum: The Cafe
---

### Post by nick167 on 2019-08-08
I just got my site manager published in the snap store ([https://snapcraft.io/install/nsm/ubuntu](https://snapcraft.io/install/nsm/ubuntu)) and would love it if people tried it out and let me know what they think. Alternatively you can build it from source, see [https://nift.cc/documentation/installing_nsm.html](https://nift.cc/documentation/installing_nsm.html). 

The official nifty site manager website is [https://nift.cc](https://nift.cc). See [https://nift.cc/resources/templates.html](https://nift.cc/resources/templates.html) for links to site repository templates on bitbucket/github/gitlab that you can import (or fork and rename) then clone using `nsm clone clone-url` to begin making websites from. 

Check out the nsm commands [https://nift.cc/documentation/nsm_commands.html](https://nift.cc/documentation/nsm_commands.html), content files [https://nift.cc/documentation/content_files.html](https://nift.cc/documentation/content_files.html), template files [https://nift.cc/documentation/template_files.html](https://nift.cc/documentation/template_files.html) and hosting your site [https://nift.cc/documentation/hosting_your_site.html](https://nift.cc/documentation/hosting_your_site.html) pages from the documentation. 

You can build updated pages for your site (after modifying the content file for a page) using `nsm build-updated`, and you can build changes locally, commit the changes to your local repository and push the changes to the remote repository all using `nsm bcp "commit message"`.

Some of the websites I've made with nsm are [https://ai-bots.net](https://ai-bots.net), [https://tron.ai-bots.net](https://tron.ai-bots.net), [https://nift.cc](https://nift.cc), [https://n-ham.com](https://n-ham.com), [https://wr3ckreational.com](https://wr3ckreational.com).

You can also find nsm on [https://staticgen.com](https://staticgen.com), please also star it on github [https://github.com/nifty-site-manager/nsm](https://github.com/nifty-site-manager/nsm) and star it on gitlab [https://gitlab.com/nifty-site-manager/nsm](https://gitlab.com/nifty-site-manager/nsm) as that's often how site managers are ranked.

Most of the other site generators/managers I have come across are highly geared towards using markdown or some other kind of template language. While nsm has syntax for inputting things like the contents of another file, path to another file, current date/time etc., you still use html or whatever language you want (by doing less here you can actually do more). I'm not sure whether the generators calling themselves static site generators are limited to just static sites or not? You should be able to use nsm for any website, static or dynamic.

Most static site generators/managers probably have similar functionality, so will come down to user preferences, I'm hoping some people prefer nsm if they try it out. I like the way templates are done for nsm (it's set up exactly how I'd guess it'd be set up, especially as a regular user of LaTeX and git) and I like how git-like using nsm is.

I would definitely love to know what people think if they have used other site generators/managers.

---

