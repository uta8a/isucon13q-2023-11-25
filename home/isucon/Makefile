.PHONY: clear_logs
clear_logs:
	sudo truncate -s 0 /var/log/nginx/isu-access.log
	sudo truncate -s 0 /var/log/mysql/mysql-slow.log

.PHONY: alp
alp:
	sudo cat /var/log/nginx/isu-access.log | alp json --sort sum -r -m '/api/livestream/\d+/statistics,/api/livestream/\d+,/api/livestream/\d+/reaction,/api/livestream/\d+/livecomment,/api/user/\w+/statistics,/api/user/\w+,/api/user/\w+/statistics,/watch/\d+' -o count,method,uri,min,avg,max,sum


.PHONY: slowlog
slowlog:
	sudo cat /var/log/mysql/mysql-slow.log | pt-query-digest
