
# run each node

iex --name node1@127.0.0.1 --cookie partitioned_cache -S mix

iex --name node2@127.0.0.1 --cookie partitioned_cache -S mix

iex --name node3@127.0.0.1 --cookie partitioned_cache -S mix

For example, from node 1 let's save some data:

```elixir
iex(node1@127.0.0.1)> PartitionedCache.put "foo", "bar"
"bar"
```

Retrieve that saved data from other node, for example from node2:

```elixir
iex(node2@127.0.0.1)> PartitionedCache.get "foo"
"bar"
```

From a different node:

```elixir
iex(node3@127.0.0.1)> PartitionedCache.get "foo"
"bar"
```