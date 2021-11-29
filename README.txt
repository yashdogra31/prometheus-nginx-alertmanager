# prometheus-nginx-alertmanager
> docker compose file created with the 3 services nginx,prometheus,alertmanager. referred docker-hub for each image details.
> edit prometheus.yml for alertmanager setup. under alerting make sure target is 'alertmanager:9093'
> now in order to monitor nginx server we need to add another container in docker-compose.yml, namely blackbox exporter.
> The blackbox exporter allows probing of endpoints over HTTP. It will get the target's metrics in the prometheus format.
> add a job named 'nginx' in prometheus.yml about the use of blackbox exporter to probe nginx container over HTTP.
> now me set up alerting rules upon which prometheus will fire alert. This is done alert.yml file. The expression 'probe_success{instance="http://nginx:80",job="nginx"} == 0' will return 0 if a service is down and 1 if up.
> when the condition is met, prometheus server will fire an alert, which is visible on alertmanager UI.
> NOTE: I used docker desktop to manually stop nginx server.

# refrences
https://prometheus.io/
https://prometheus.io/docs/alerting/latest/alertmanager/
https://www.digitalocean.com/community/tutorials/how-to-use-alertmanager-and-blackbox-exporter-to-monitor-your-web-server-on-ubuntu-16-04
https://hub.docker.com/r/prom/alertmanager
https://hub.docker.com/r/prom/prometheus
https://hub.docker.com/_/nginx
https://hub.docker.com/r/prom/blackbox-exporter/
