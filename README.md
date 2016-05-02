#### pknginxtbshoot
#####2 searching for problems
log_format
```
log_format combined '$remote_addr - $remote_user [$time_local]'   '"$request"  $status  $body_bytes_sent ' '"$http_referer" "http_user_agent"';
```
other variables
[see here](http://nginx.org/en/docs/http/ngx_http_core_module.html)
```
$gzip_ratio
$msec
$request_length
$request_time
$content_type
```

Logging POST requests(should declare in higher context)
```
log_format myformat 'body: "$request_body"';
```
```
access_log /var/log/nginx/requests.log myformat;
```

map: ngx_http_map_module  
  
if set a variable
```
access_log /var/log/nginx/requests.log myformat if=$myflag;
```

set $myflag var:
```
map $request_method $myflag{
  POST 1;
  default 0;
}
```
