
### **Level 1: Basic Concepts (Understanding the 'Why')**

1. **What is the difference between Synchronous and Asynchronous programming in Python?**
* *Focus:* Blocking vs. Non-blocking I/O operations.


2. **Why do we use Async for Database operations instead of Multi-threading?**
* *Focus:* Context switching overhead and the Global Interpreter Lock (GIL) in Python.


3. **What is an Event Loop in Python's `asyncio`?**
* *Focus:* How the loop manages and schedules different tasks.


4. **What are `async` and `await` keywords?**
* *Focus:* Defining coroutines and yielding control back to the event loop.



---

### **Level 2: Intermediate (Connection Pooling & Resource Management)**

5. **What is Connection Pooling, and why is it critical for Production databases?**
* *Focus:* The cost of TCP handshakes and creating/destroying connections repeatedly.


6. **How does a Connection Pool handle 'Maximum Overflow' and 'Pool Size'?**
* *Focus:* Managing peak traffic without crashing the database.


7. **What happens if a connection in the pool becomes "stale" or "idle"?**
* *Focus:* `pool_recycle` and connection validation.


8. **Difference between `psycopg2` and `asyncpg`?**
* *Focus:* `asyncpg` is built specifically for async from the ground up and is significantly faster.



---

### **Level 3: Advanced (Performance & Concurrency)**

9. **What is the 'Thundering Herd' problem in connection pooling?**
* *Focus:* Many processes waking up at once to grab a resource.


10. **How do you handle Database Migrations or Schema changes in an Async environment?**
* *Focus:* Using tools like `Alembic` with async drivers.


11. **How would you debug a Deadlock in an Asynchronous database transaction?**
* *Focus:* Understanding transaction isolation levels and async task cancellation.


12. **Explain 'Backpressure' in the context of Async Data Pipelines.**
* *Focus:* What happens when the database can't keep up with the incoming async requests.


13. **Why is `pd.read_sql()` technically "blocking" even if called inside an `async def` function?**
* *Focus:* Pandas is synchronous; you need to run it in a separate thread/executor or use an async-native way to fetch data.



---

### **Level 4: Scenario-based (Production Level)**

14. **"If your Streamlit app has 100 concurrent users, how would you configure your SQLAlchemy Async Engine?"**
* *Focus:* Setting `pool_size` vs `max_overflow`.


15. **"You noticed your DB CPU is at 90% after switching to Async. What could be the reason?"**
* *Focus:* Too many concurrent queries being fired because there's no "blocking" to slow them down.


16. **"Explain the difference between `asyncio.gather()` and `asyncio.wait()` when executing multiple SQL queries."**
* *Focus:* Error handling and waiting for all vs. some tasks.

---
ইন্টারভিউয়ার যদি জিজ্ঞেস করে, "What is the difference between backref and back_populates?"
    উত্তর: backref পুরনো স্টাইল, যেখানে এক জায়গায় লিখলেই অন্য পাশে অটোমেটিক অ্যাট্রিবিউট তৈরি হয়ে যেত। কিন্তু back_populates হলো মডার্ন (SQLAlchemy 2.0 স্টাইল), যেখানে দুই পাশেই ম্যানুয়ালি ডিফাইন করতে হয়। এতে কোড অনেক বেশি Explicit এবং Readable হয়, যা বড় প্রজেক্টের জন্য বেস্ট।

    