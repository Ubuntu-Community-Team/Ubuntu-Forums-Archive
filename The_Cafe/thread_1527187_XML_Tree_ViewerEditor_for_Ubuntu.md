---
title: "XML Tree Viewer/Editor for Ubuntu"
date: 2010-07-09
forum: The Cafe
---

### Post by Simon Cropper on 2010-07-09
Hi,

I have what I thought would be a simple problem but after many hours of searching and trials I have discovered it is actually quite a difficult problem.

Basics: I have a range of hierarchical XML files containing a variety of data sets. One in particular includes projects-taskgroups-tasks-subtasks, all with different attributes (e.g. due date, hours, contact, hyperlinks). I also have XML representing taxonomic trees for plants and animals.

Wants: I want to open any of these XML files and view as a tree grid, that is a grid with columns representing attributes and rows projects, taskgroups, tasks and subtasks (indented correctly). Children should be able to be dragged and dropped onto different parents, and new nodes added/deleted/ renamed quickly. Preferably some level of formatting would be desirable. Cells in the row-column intersect should be editable and new attributes (i.e. column or attributes) should be able to be added, deleted and edited.

Summary: A generic spreadsheet that is XML aware.

Solutions available: No generic options have been found. A number of people have created specialty solutions (e.g. TaskCoach) using wxPython and there are graphical editors around with some of this functionality (Get Things Gnome, GnoTime) but there is no generic interactive package available (that I have been able to find).

Any help or suggestions would be appreciated.

Simon

---

### Post by tvardovsky on 2010-07-12
I am quite sorry to see no replies just yet - I am also interested in an application with this functionality for a number of projects I am working on.

I'll keep my eyes open and send along anything I find that I deem at all helpful.

Good luck with your project.

:cool:

---

### Post by KIAaze on 2010-07-12
Packages:
```
xmlcopyeditor
kxmleditor

```
kxmleditor is apparently not available anymore since dapper (but it is still available on the latest OpenSUSE!).

Did a search for "linux xml editor" on google not give any satisfying results?

Links for several XML editors:
[http://xml-copy-editor.sourceforge.net/](http://xml-copy-editor.sourceforge.net/)
[http://kxmleditor.sourceforge.net/](http://kxmleditor.sourceforge.net/)
[http://www.screem.org/](http://www.screem.org/)
[http://www.oxygenxml.com/download.html](http://www.oxygenxml.com/download.html)
[http://www.editix.com/](http://www.editix.com/)

---

### Post by Simon Cropper on 2010-07-12
> **KIAaze said:**
> Packages:
```
xmlcopyeditor
kxmleditor

```

Did a search for "linux xml editor" on google not give any satisfying results?



No it did't. Searches either ended in non-free products or not meeting my specifications... 

> Wants: I want to open any of these XML files and **view as a tree grid**, that is a grid with columns representing attributes and rows projects, taskgroups, tasks and subtasks (indented correctly). Children should be able to be dragged and dropped onto different parents, and new nodes added/deleted/ renamed quickly. Preferably some level of formatting would be desirable. Cells in the row-column intersect should be editable and new attributes (i.e. column or attributes) should be able to be added, deleted and edited.


Yes, there are a range of editors out their that allow you to view XML, but none in a human friendly way and none are designed to allow you to manipulate the data in the way described above.


I suppose the distinction is between 'viewing / checking validity' and 'data entry / visualization / manipulation' in a easy to use GUI interface.

Simon

---

### Post by WolfRage on 2010-11-30
Hi I know this is an older post, but I found my perfect solution in "TreeLine" check it out, it is in the repos. It is a great little program. Take the time to get fimiliar with it by building a new empty document, and make sure you use the "Configure Data Types" to make your own data types. It is super easy to setup and can help you build an XML database or document in no time, and is very easy to use. Just use the export feature to save as XML when you are ready.

---

### Post by Simon Cropper on 2010-11-30
WolfRage,

I had also discovered TreeLine and yes it is a good program.

Treeline contains two panes - the left is a tree and the right a list of customized fields for the record highlighted in the left pane.

What I wanted is the right pane to be a spreadsheet type of look with column representing fields. Ideally the fields could be sorted by clicking on the header. So for example you could have a list of tasks grouped into broad projects in the right pane and a list of tasks in the right pane tallied under one another - fields could be priority, date start, data finish, task, etc. If you look at [TaskCoach]("http://www.taskcoach.org/") it has something like this.

What I was after was a generic 'database' using the XML model, like TaskCoach but generic so you could use any fields you wanted.

TreeLine was the closest I got to a solution.

Cheers Simon

---

