READEX specifics
=============

Compilation
-------------
The plugin *must* be compiled with `ENABLE_MPI`

Usage during Design Time Analysis with Periscope
-------------
For READEX purposes, we use the hdeem_sync_plugin, which enables us to attribute energy to specific regions. To use the plugin, it must be enabled during runs with Periscope. To do so, use the following environment variables:
```
export SCOREP_METRIC_PLUGINS=hdeem_sync_plugin
export SCOREP_METRIC_PLUGINS_SEP=";"
export SCOREP_METRIC_HDEEM_SYNC_PLUGIN_CONNECTION="INBAND"
export SCOREP_METRIC_HDEEM_SYNC_PLUGIN_VERBOSE="WARN"
export SCOREP_METRIC_HDEEM_SYNC_PLUGIN_STATS_TIMEOUT_MS=1000
```
Furthermore, the metric source definition of your `readex_config.xml` should look like this:
```
<metricPlugin>
  <name>hdeem_sync_plugin</name>
</metricPlugin>
<metrics>
  <node_energy>hdeem/BLADE/E</node_energy>
  <cpu0_energy>hdeem/CPU0/E</cpu0_energy>
  <cpu1_energy>hdeem/CPU1/E</cpu1_energy>
</metrics>
```
