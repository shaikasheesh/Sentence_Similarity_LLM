# Sentence_Similarity_LLM

Here is the problem statement:
Customers Need Help Searching Product Catalogs
With the rapid expansion of online activity in the last few years, more and more customers are engaging online outlets for a wider range of needs. In response, many organizations have rapidly expanded the range of content and goods they make available online to better ensure customers have access to the items they want

While more is often better, many online sites hit a tipping point beyond which the number of offerings make it actually harder for customers to find what they are looking for. Without the precise terms to locate a specific widget or an article on a narrowly defined topic, consumers find themselves frustrated scrolling through lists of items that just aren’t quite right

Solution Approach:
Using LLMs, we can task a model with poring over product descriptions, written content or the transcripts associated with audio recordings and responding to user searches with suggestions for things relevant to their prompts. 

Users don’t need the precise terms to find what they are looking for, just a general description with which the LLM can orient itself to their needs. The end result is a powerful new experience that leaves users feeling as if they have received personalized, expert guidance as they engage the site.

Now,
for this use case I have taken wayfair annotation data set, which consists of three csv files.

Product --> contains products related info such as prod id, prod description, prod name

Query --> contains the query and query class

Labels --> contains prod id, query id, labels (exact, irrelevant, partial)

We need queries similarly matching to the products information.

The idea is to take an pretrained LLM model which needs to work on Sentence similarity task and fine tune it for the Wayfair data set.

Steps:
Download the data set
create the input documents
select the embedding model
store the embedding vectors to the vector database
Perform similarity search with score using the query to get the top products matching along with the distance score.

Now for the fine tuning,
Using InputExamples library from sentence transformers format the inputs (Query, product description,labels).

Use Dataloader to feed this data in batches to the LLM model. Evaluate the sentence similarity model using cosine similarity loss.

After fine tuning, compare the base model and fine tuned model using the cosine similarity loss and we also try to find out the correlation coeff for the labels and cosine similarity scores.

Go through the notebook for the code and try it for different ecomm data set out there to get the understanding in more better way. 

Simply, we are performing semantic search instead of keyword based search to improve the customer experience with help of LLM.
