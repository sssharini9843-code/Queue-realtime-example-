class Node:
def __init__(self, data):
self.data = data
self.next = None

class QueueADT:
def __init__(self):
self.front = self.rear = None

def enqueue(self, data):
"""Add a job to the end of the queue (O(1))"""
new_node = Node(data)
if self.rear is None:
self.front = self.rear = new_node
print(f"Added Job: '{data}' to the queue.")
return
self.rear.next = new_node
self.rear = new_node
print(f"Added Job: '{data}' to the queue.")

def dequeue(self):
"""Process the job at the front of the queue (O(1))"""
if self.front is None:
return "Queue Underflow (No jobs to process)"

temp = self.front
self.front = self.front.next

# If queue becomes empty, update rear to None
if self.front is None:
self.rear = None

return temp.data

def display(self):
"""Show all pending jobs in the queue"""
if self.front is None:
print("\nQueue is empty.")
return

print("\n--- Current Queue (Front to Rear) ---")
curr = self.front
while curr:
print(f"[{curr.data}]", end=" <- ")
curr = curr.next
print("End")

# --- Real-Time Simulation ---
if __name__ == "__main__":
q = QueueADT()

# 1. Adding jobs (Enqueue)
q.enqueue("Print Document_1.pdf")
q.enqueue("Print Photo_Holiday.jpg")
q.enqueue("Print Spreadsheet_Report.xlsx")

# 2. Displaying current state
q.display()

# 3. Processing jobs (Dequeue)
print(f"\nProcessing: {q.dequeue()}")
print(f"Processing: {q.dequeue()}")

# 4. Final state
q.display()

# 5. Adding another job
q.enqueue("Print Email_Confirmation.pdf")
q.display()



Output:
Added Job: 'Print Document_1.pdf' to the queue.
Added Job: 'Print Photo_Holiday.jpg' to the queue.
Added Job: 'Print Spreadsheet_Report.xlsx' to the queue.

--- Current Queue (Front to Rear) ---
[Print Document_1.pdf] <- [Print Photo_Holiday.jpg] <- [Print Spreadsheet_Report.xlsx] <- End

Processing: Print Document_1.pdf
Processing: Print Photo_Holiday.jpg

--- Current Queue (Front to Rear) ---
[Print Spreadsheet_Report.xlsx] <- End

Added Job: 'Print Email_Confirmation.pdf' to the queue.

--- Current Queue (Front to Rear) ---
[Print Spreadsheet_Report.xlsx] <- [Print Email_Confirmation.pdf] <- End
 
