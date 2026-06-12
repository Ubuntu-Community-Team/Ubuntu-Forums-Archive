---
title: "Suggestions for a Wiki+Forum Site?"
date: 2005-07-29
forum: The Cafe
---

### Post by jdong on 2005-07-29
Hey, I'm sure we have some website designers in here who would know their ropes with the OSS website solutions:

I'm looking for a website system for our robotics team that could accomplish the following tasks:

```

Feature List:

    * Front page with a description of the team, pictures of team members / robots, links to:
    * Team Members' area: Area for our team members to communicate with each other. When necessary, some pages should be private and not readable by the general public. This will also contain a calendar or timeline of some sort, so everyone has a single bookmarked page to check for the next meeting date(s)
    * Forum. Probably PHPBB2 (the forum system we currently use), but most content will probably not survive the migration. The forum should support attaching files for team members to share stuff with each other.
    * Ability to upload files to the Wiki area, so one can post files for download. This should be restrictable, too, by membership status and by file size.
    * Project Management Area: For core team members, access to a web-based project management system with task assignments, Gantt Charts, and other planning stuff

```

The system should be Wiki-based for the main site areas (or Wiki-like, so others can contribute). The forum and Project Management doesn't have to integrate with the Wiki or each other; that's fine :)

This will be hosted on a LAMP server, with MySQL and POSSIBLY CGI.

What are your recommendations for what software package(s) I should use?

---

### Post by DJ_Max on 2005-07-29
What language do you want your CGI written in, if any, do you plan to use? Also, for a forum I would use [SMF](http://simplemachines.org/). For project managment, look at [Trac](www.edgewall.com/trac/). It has a built-in wiki as well, also runs in CGI, but not recommended.

---

