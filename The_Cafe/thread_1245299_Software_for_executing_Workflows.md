---
title: "Software for executing Workflows"
date: 2009-08-20
forum: The Cafe
---

### Post by cudjoe on 2009-08-20
I am thinking of implementing a (simple) workflow software.
I better consult you guyz to know what already exists in the jungle.

The concept is simple : 
I draw a flow chart (graph with nodes and directed edges).
For each node I can specify a command to run. The output of the node command will be piped to the input of following nodes.

Google did not help me much in finding this.

I found phatch which somehow does this for images, but I would like something generic and that is not limited to linear flow (i.e. nodes can be run in parallel, execution of following node starts when all inputs ready)

Technically, I would imagine something very simple :
 - a canvas widget for nodes and edges
 - a tab widget with command field and parameters
Cherry-on-top : 
 - a script API to bring to GUI some infos like input,output and parameters help, logging,etc.

---

### Post by koenn on 2009-08-20
maybe jboss workflow engine ? 
[http://www.jboss.com/products/jbpm/](http://www.jboss.com/products/jbpm/)

---

### Post by cudjoe on 2009-08-21
I was thinking of something smaller... a light GUI without Application server etc.

I'll make a prototype using something like this (Qt4 scenes) :
[http://doc.trolltech.com/4.3/graphicsview-diagramscene.html](http://doc.trolltech.com/4.3/graphicsview-diagramscene.html)

---

### Post by cudjoe on 2010-04-19
I made a workflow editor and runner, using Python, with a Qt4 GUI.

[Project page : **florun**]("http://bit.ly/b07iD2")

It is released under GPL, feel free to try it or contact me ! or [view the demo screencast]("http://bit.ly/awEUCo")

---

