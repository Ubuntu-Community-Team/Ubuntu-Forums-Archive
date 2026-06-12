---
title: "QT4, Mysql plugin, and  libmysqlclient15 / Memory Leaks"
date: 2009-05-04
forum: Ubuntu Dev Link Forum
---

### Post by Doctor X on 2009-05-04
I've written some software internally, which uses QT4 and more specifically the Mysql plugin for Qt4. I recently upgraded a computer to Jaunty, and recompiled my software on the new system.

After running the newly recompiled software on Jaunty, I noticed huge memory leaks occuring as the program runs. When linked to previous versions of QT4, my software did not display any memory leaks over 2-3 years of daily use.

At a certain point, the program runs out of RAM, and all further SQL transactions fail. However, the rest of the program chugs along as if nothing has happened (no allocation of ram from the heap takes place in the other parts of the program)

I installed Valgrind, and checked for memory leaks. Over a 3 hour period, I'm losing roughly 800 Megabytes of ram to leaks.

a portion of the Valgrind log says (trimmed for brevity)

==32589== 807,250,448 (4,482,456 direct, 802,767,992 indirect) bytes in 50,937 blocks are definitely lost in loss record 159 of 161
==32589==    at 0x4026FDE: malloc (vg_replace_malloc.c:207)
==32589==    by 0x4DB82DC: my_malloc (in /usr/lib/libmysqlclient_r.so.15.0.0)
==32589==    by 0x4DDF380: mysql_store_result (in /usr/lib/libmysqlclient_r.so.15.0.0)
==32589==    by 0x4CDCEC9: (within /usr/lib/qt4/plugins/sqldrivers/libqsqlmysql.so)
==32589==    by 0x4055FAD: QSqlQuery::exec(QString const&) (in /usr/lib/libQtSql.so.4.5.0)
==32589==    by 0x80564B2: ProgramDBConn::checkOrAddLeave(QSqlQuery&, int) (programdbconn.cpp:407)
==32589==    by 0x8056FAA: ProgramDBConn::leave(int, int) (programdbconn.cpp:316)

The functions themselves are pretty simple.

void ProgramDBConn::leave(int, int argument)
{
    QSqlQuery query(db);

    checkOrAddLeave(query, argument);

    QString update = QString("UPDATE Leaves SET TimesLeft=TimesLeft+1 WHERE Arg=%1")
            .arg(argument);

    if (!query.exec(update))
    {
        std::cout << "! ERROR '" << db.lastError().text().toStdString() << "' with '" << update.toStdString() << "'" << std::endl;
        emit dbError(db.lastError().number());
    }
}

void ProgramDBConn::checkOrAddLeave(QSqlQuery& query, int argument)
{
    // check to see if we have a proper entry in the table to update
    QString check = QString("SELECT Arg FROM Leaves WHERE Arg=%1").arg(argument);

    if (query.exec(check) && query.next())
    {
        // arg is valid, lets skip the rest
        // this path is taken for all but one call per year...
    }
    else // create the entry for the year
    {
        QString insert = QString("INSERT INTO Leaves (Arg, TimesLeft, TimesEncountered) VALUES (%1, 0, 0)").arg(argument);

        if (!query.exec(insert))
        {
            std::cout << "! ERROR '" << db.lastError().text().toStdString() << "' with '" << insert.toStdString() << "'" << std::endl;
            emit dbError(db.lastError().number());
        }
    }
}

I changed the code slightly for brevity, so please forgive any typos. It has compiled and worked, and without leaks that I've encountered recently.

Am I doing something wrong within these two functions that would lead to a leak?  I'm assuming, that once we return from leave(int,int) that the destructor for QSqlQuery will clean itself up.

Regards

---

