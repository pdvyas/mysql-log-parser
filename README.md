Mysql Log parser
----------------

Retrieved from mysql-utilities (possibly bundled with MySQL workbench) and made
changes for Percona's slow log.

Usage
-----
Example file

```
# Time: 130131 11:09:34
# User@Host: det5mcxkw6dhenf6[det5mcxkw6dhenf6] @ localhost []
# Thread_id: 11441651  Schema: det5mcxkw6dhenf6
# Query_time: 6.058117  Lock_time: 0.000000  Rows_sent: 0  Rows_examined: 0  Rows_affected: 0  Rows_read: 1
use det5mcxkw6dhenf6;
commit;
```

### Shell Example

```
In [1]: from mysql_log_parser.parser import SlowQueryLog

In [2]: f = open('mysql-slow-query.log')

In [3]: log = SlowQueryLog(f)

In [4]: log.next()
Out[4]: 
{'database': 'det5mcxkw6dhenf6;',
 'datetime': datetime.datetime(2013, 1, 31, 11, 9, 34),
 'host': 'localhost',
 'lock_time': Decimal('0.000000'),
 'query': 'use det5mcxkw6dhenf6;\ncommit;',
 'query_time': Decimal('6.058117'),
 'rows_affected': 0,
 'rows_examined': 0,
 'rows_read': 1,
 'rows_sent': 0,
 'schema': 'det5mcxkw6dhenf6',
 'session_id': None,
 'thread_id': '11441651',
 'user': 'det5mcxkw6dhenf6'}
```
