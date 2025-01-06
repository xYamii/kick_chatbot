# KickClient

KickClient is a WebSocket-based library for interacting with Kick chatrooms.

## Features

- Subscribe to chatrooms.
- Receive and process messages in real-time.

## Example

```rust
use kick_client::KickClient;

#[tokio::main]
async fn main() {
    let client = KickClient::new("wss://ws-us2.pusher.com/app/32cbd69e4b950bf97679?protocol=7&client=js&version=8.4.0-rc2&flash=false");
    let mut messages = client.connect(12345).await.unwrap();

    while let Some(message) = messages.recv().await {
        println!("{:?}", message);
    }
}