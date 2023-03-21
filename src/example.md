use mini_redis::{client::{self, Client},Result};

#[tokio::main]
async fn main() -> Result<()> {
    let mut client: Client = client::connect("127.0.0.1:6379").await?;
    client.set("hello","tokio".into()).await?;
    let result = client.get("hello").await?;
    println!("got value from server : {:?} ",result);
    Ok(())  
}
