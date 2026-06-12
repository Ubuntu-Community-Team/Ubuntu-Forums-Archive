---
title: "QT4 designer- Laucnch one window from another"
date: 2011-05-28
forum: Ubuntu Dev Link Forum
---

### Post by ankeetg on 2011-05-28
Hey!

I'm just getting a hang of qt4 using the designer and I've reached the coding part.

I suspect this should be an easy one to solve..

Here's my thing.. I have two files..
**objectname:** windowStart
**objectname:** windowAddCluster

I have a next button in windowStart

Can I know how to code my button such that on click it opens windowAddCluster
What code should I put in addCluster() in guistart.cpp?

[SIZE=3]**guistart.h**[/SIZE]
```
#ifndef GUISTART_H
#define GUISTART_H
 
#include "ui_guistart.h"
 
 
class guiStart : public QMainWindow, private Ui::windowStart
{
    Q_OBJECT
 
public:
    guiStart(QMainWindow *parent = 0);
 
 
public slots:
    void addCluster();
};
 
 
#endif
```[SIZE=3]**addcluster.h**[/SIZE]
```
#ifndef ADDCLUSTER_H
#define ADDCLUSTER_H
 
#include "ui_addcluster.h"
 
 
class addCluster : public QMainWindow, private Ui::windowAddCluster
{
    Q_OBJECT
 
public:
    addCluster(QMainWindow *parent = 0);
 
 
public slots:
    //void addCluster();
};
 
 
#endif
```[SIZE=3]**guistart.cpp**[/SIZE]
```
#include <QtGui> 
#include "guistart.h"
#include "addcluster.h"

// if we include <QtGui> there is no need to include every class used: <QString>, <QFileDialog>,...
 
guiStart::guiStart(QMainWindow *parent)
{
    setupUi(this); // this sets up GUI
 
    // signals/slots mechanism in action
    connect( nextButton, SIGNAL( clicked() ), this, SLOT( addCluster() ) );  
}
 
 
void guiStart::addCluster()
{
    addCluster *dialog = new addCluster;
     dialog->show();
    //addCluster dialog(this); 
    //dialog.exec();
}
```[SIZE=3]**addcluster.cpp**[/SIZE]
```
#include "addcluster.h" 
 
addCluster::addCluster(QMainWindow *parent) 
{ 
    setupUi(this); 
} 

```[SIZE=3]**main.cpp**[/SIZE]
```
#include <QApplication>
 
#include "guistart.h"
 
int main(int argc, char *argv[])
{
        QApplication app(argc, argv);
     guiStart *dialog = new guiStart;
     dialog->show();
    app.connect(&app, SIGNAL(lastWindowClosed()), &app, SLOT(quit()));
    return app.exec();
}
    
```any help would be great guys!
Thanks!

---

### Post by ankeetg on 2011-05-28
I got it working..common C++ errors...shifting to C++ from C after years..

New question..what is the qt4 function to close a window?
is it close()?

---

