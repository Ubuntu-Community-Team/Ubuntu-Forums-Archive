---
title: "statistics in postgresql 8.3 in 8.04.1"
date: 2009-03-02
forum: Server Platforms
---

### Post by leticia2602 on 2009-03-02
Hello

I want to see statistics about the use of my postgresql 8.3 in Ubuntu 8.04.1 (Hardy) Server. The package installed is [http://packages.ubuntu.com/hardy/postgresql](http://packages.ubuntu.com/hardy/postgresql) 

In my postgresql.conf I have the follow configuration related to statistics (the default configuration):

"""
#---------------------------------------------------------------------------
---
# RUNTIME STATISTICS
#---------------------------------------------------------------------------
---

# - Query/Index Statistics Collector -

#track_activities = on
#track_counts = on
#update_process_title = on


# - Statistics Monitoring -

#log_parser_stats = off
#log_planner_stats = off
#log_executor_stats = off
#log_statement_stats = off
""""

But when I execute this command "select * from pg_stat_all_tables;" I get all the rows with the values (except the 3 first values) set to 0:

"""
relid | schemaname | relname | seq_scan| seq_tup_read | idx_scan | idx_tup_fetch | n_tup_ins | n_tup_upd | n_tup_del | n_tup_hot_upd | n_live_tup | n_dead_tup | last_vacuum | last_autovacuum | last_analyze | last_autoanalyze
--------+--------------------+-------------------------------------+----
11444  | information_schema | sql_packages   | 0 | 0 |   |   | 0 | 0 | 0 | 0 | 0 | 0 |  |  |  |
11431  | pg_toast 	    | pg_toast_11429 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |  |  |  |
153470 | pg_toast           | pg_toast_153466| 0 | 0 | 0 | 0 | 0 | 0 |   | 0 | 0 | 0 |  |  |  |
"""

What I need to do to obtain the values updated in pg_stat_all_tables?
Or the statistic are stored in other place??

The statistic in this version of postgres are by default enabled, but I didn't see values different to 0 in previous table, neither the process "postgres: stats collector process" as say in [http://www.postgresql.org/docs/8.3/static/monitoring-ps.html](http://www.postgresql.org/docs/8.3/static/monitoring-ps.html) is running in my server.


Thanks in advanced.

Leticia Larrosa

---

