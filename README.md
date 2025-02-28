# Grafana Cheatsheet

## **Grafana Overview**
Grafana is an open-source visualization tool for monitoring and observability, used to create dashboards with data from various sources like Prometheus, Elasticsearch, and more.

---

## **Grafana Installation & Setup**
```sh
sudo apt-get install -y grafana     # Install Grafana on Debian-based systems
sudo systemctl start grafana-server # Start Grafana service
sudo systemctl enable grafana-server # Enable Grafana on startup
```

### **Access Grafana UI**
- Default URL: `http://localhost:3000`
- Default credentials: `admin / admin`

---

## **Adding Data Sources**
1. Go to **Configuration > Data Sources**
2. Click **Add data source**
3. Select the desired data source (e.g., Prometheus, InfluxDB, MySQL)
4. Configure the connection settings and save

### **Example: Adding Prometheus as a Data Source**
```yaml
url: http://localhost:9090
scrape_interval: 15s
```

---

## **Creating Dashboards & Panels**
1. Navigate to **Create > Dashboard**
2. Click **Add new panel**
3. Choose a data source and enter a query
4. Customize visualization settings (Graph, Gauge, Table, etc.)
5. Click **Apply** to save the panel

### **Common Panel Queries (PromQL)**
```sh
rate(http_requests_total[5m])   # Requests per second over 5 minutes
sum by(instance) (node_cpu_seconds_total)  # CPU usage by instance
avg_over_time(node_memory_used_bytes[10m])  # Average memory usage over 10 minutes
```

---

## **Setting Up Alerts**
1. Go to **Alerting > Alert Rules**
2. Click **Create Alert Rule**
3. Define the conditions (e.g., when CPU usage exceeds a threshold)
4. Set up **Notification Channels** (Slack, Email, PagerDuty, etc.)
5. Save and enable the alert

### **Example Alert Rule**
```yaml
expr: avg_over_time(node_memory_used_bytes[5m]) > 80
for: 5m
labels:
  severity: critical
annotations:
  description: "Memory usage is above 80% for the last 5 minutes"
```

---

## **Grafana CLI Commands**
```sh
grafana-cli plugins list        # List installed plugins
grafana-cli plugins install <plugin-name>  # Install a new plugin
grafana-cli admin reset-admin-password <new-password>  # Reset admin password
```

---

## **Useful Grafana Resources**
- [Grafana Docs](https://grafana.com/docs/)
- [Grafana Plugins](https://grafana.com/grafana/plugins/)
- [Grafana Alerting](https://grafana.com/docs/grafana/latest/alerting/)

---

This cheatsheet provides a quick reference for Grafana setup, dashboards, queries, and alerts. Let me know if you need any modifications!

