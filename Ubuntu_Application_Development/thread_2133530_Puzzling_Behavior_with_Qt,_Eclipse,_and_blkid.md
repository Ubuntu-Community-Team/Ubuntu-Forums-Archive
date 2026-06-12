---
title: "Puzzling Behavior with Qt, Eclipse, and blkid"
date: 2013-04-08
forum: Ubuntu Application Development
---

### Post by elemings on 2013-04-08
Below is the source code for a simple little Qt for Embedded Linux program (built with qvfb drivers) that calls a single function from the blkid API.

```
::::::::::::::
CMakeLists.txt
::::::::::::::


cmake_minimum_required ( VERSION 2.8 )


find_package ( Qt4 REQUIRED QtCore QtGui )
include ( UseQt4 )


qt4_wrap_cpp ( MOC_SOURCES
    window.h
)


add_executable ( test02
    main.cpp
    window.cpp
    ${MOC_SOURCES}
)


target_link_libraries ( test02
    ${QT_LIBRARIES}
    blkid
)


::::::::::::::
main.cpp
::::::::::::::


#include <stdio.h>


#include <blkid/blkid.h>


#include <QtGui/QApplication>


#include "window.h"


void stderr_msg_handler (QtMsgType /*unused*/, char const* msg)
{
    const char* fmt = "(yyyy-MM-dd HH:mm:ss.zzz) ";
    const QString now (QDateTime::currentDateTime().toString(fmt));
    fputs (now.toUtf8().constData(), stderr);
    fputs (msg, stderr);
    fputc ('\n', stderr);
}


void dumpFsType (const char* devPath)
{
    const char* fsType = blkid_get_tag_value( NULL, "TYPE", devPath );
    qDebug() << "devPath " << QString(devPath) << ", "
             << "fsType " << (NULL == fsType? "NULL value": QString(fsType));
}


int main (int argc, char** argv)
{
    /*QtMsgHandler oldMsgHandler =*/ qInstallMsgHandler (stderr_msg_handler);
    dumpFsType ("/dev/sdb1");


    QApplication app (argc, argv);
    Window wnd;
    wnd.show();
    int status = app.exec();


    dumpFsType ("/dev/sdb1");
    return status;
}


::::::::::::::
window.cpp
::::::::::::::


#include <blkid/blkid.h>


#include "window.h"


Window::Window (QWidget* parent)
    : QWidget (parent)
    , lineEdit(0), resultLabel(0)
{
    QVBoxLayout* vbox = new QVBoxLayout;
    lineEdit = new QLineEdit (tr ("Device Pathname"));
    vbox->addWidget (lineEdit);


    QPushButton* pushButton = new QPushButton (tr ("&Execute"));
    connect (pushButton, SIGNAL(clicked()),
             this, SLOT(setText()));
    vbox->addWidget (pushButton);


    resultLabel = new QLabel (tr ("Result"));
    vbox->addWidget (resultLabel);
    vbox->addStretch (1);
    setLayout (vbox);


    setWindowTitle (tr ("test02"));
    //resize (240, 160);
}


void Window::setText()
{
    const QString qstr = lineEdit->text();
    const char* devPath = qstr.toUtf8().constData();
    const char* fsType = blkid_get_tag_value( NULL, "TYPE", devPath );
    resultLabel->setText (NULL == fsType? "NULL value": QString(fsType));
}
::::::::::::::
window.h
::::::::::::::


#ifndef WINDOW_H_
#define WINDOW_H_


#include <QtGui/QtGui>


class Window
    : public QWidget
{
    Q_OBJECT


public:
    Window (QWidget *parent = 0);


private:
    QLineEdit*      lineEdit;
    QLabel*         resultLabel;


private slots:
    void setText();
};


#endif /* WINDOW_H_ */

```

Here's a few commands to setup a debug session in Eclipse:

```
export QTDIR=/usr/local/qt/4.7.3-embedded-qvfb
export PATH=${QTDIR}/bin:${PATH}
cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug ../../Sources/test02 >& cmake.out.1 &
sudo eclipse &
sudo /usr/local/qt/4.7.3-x11/bin/qvfb -width 1024 -height 768 -depth 16 &
```

After importing the CMake-generated Eclipse project, I create a new Debug Configuration for the program with command-line arguments:

```
-qws -display QVFb:0
```

When stepping through the code, the puzzling behavior is that the blkid function returns expected values outside of the Qt main loop but within the Qt main loop the function stores an empty string in the device path input parameter (which should be impossible considering the input string is const char*) and returns a NULL value.

I'm gussing blkid is not thread-safe and Qt threads are causing the odd behavior.  Should I be using some sort of mutex here? How do I fix this problem?

Any and all advice appreciated.

---

