---
title: EXECUTE | TiDB SQL Statement Reference
summary: An overview of the usage of EXECUTE for the TiDB database.
category: reference
---

# EXECUTE

The `EXECUTE` statement provides an SQL interface to server-side prepared statements.

## Synopsis

**ExecuteStmt:**

![ExecuteStmt](/media/sqlgram-v3.0/ExecuteStmt.png)

**Identifier:**

![Identifier](/media/sqlgram-v3.0/Identifier.png)

## Examples

```sql
mysql> PREPARE mystmt FROM 'SELECT ? as num FROM DUAL';
Query OK, 0 rows affected (0.00 sec)

mysql> SET @number = 5;
Query OK, 0 rows affected (0.00 sec)

mysql> EXECUTE mystmt USING @number;
+------+
| num  |
+------+
| 5    |
+------+
1 row in set (0.00 sec)

mysql> DEALLOCATE PREPARE mystmt;
Query OK, 0 rows affected (0.00 sec)
```

## MySQL compatibility

This statement is understood to be fully compatible with MySQL. Any compatibility differences should be [reported via an issue](/v3.1/report-issue.md) on GitHub.

## See also

* [PREPARE](/v3.1/reference/sql/statements/prepare.md)
* [DEALLOCATE](/v3.1/reference/sql/statements/deallocate.md)
